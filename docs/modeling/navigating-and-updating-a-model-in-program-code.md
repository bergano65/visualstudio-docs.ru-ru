---
title: Перемещение по модели и обновление модели в коде программы
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af0bd2c315114444057ca05e9bb85691fe72e966
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416248"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Работа с моделями и изменение их в коде программы

Можно написать код, чтобы создавать и удалять элементы модели, задавать их свойства и удалить связи между элементами. Все изменения должны вноситься в рамках транзакции. Если элементы можно просматривать на схеме, диаграмме будет «корректировке» автоматически в конце транзакции.

##  <a name="example"></a> Примере рассмотрено определение DSL
 Это основная часть DslDefinition.dsl в примерах этого раздела:

 ![Схема определения DSL &#45; модель семейного дерева](../modeling/media/familyt_person.png)

 Эта модель является экземпляром данного DSL:

 ![Модель1 семейного древа Тюдор](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Ссылки и пространства имен
 Чтобы запустить код в этом разделе, следует ссылаться на:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Код будет использовать это пространство имен:

 `using Microsoft.VisualStudio.Modeling;`

 Кроме того при написании кода в виде отдельного проекта, от того, в которой определен доменный язык, следует импортировать сборки, построенные проектом Dsl.

##  <a name="navigation"></a> Перемещение модели

### <a name="properties"></a>Свойства
 Свойства домена, определенные в определении DSL становятся свойствами, которые доступны в программном коде:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Если вы хотите задать свойство, это необходимо сделать внутри [транзакции](#transaction):

 `henry.Name = "Henry VIII";`

 Если в определении DSL, свойство элемента **вид** — **Calculated**, задать его невозможно. Дополнительные сведения см. в разделе [вычисляемые и пользовательские свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Отношения
 Доменные связи, определенные в определении DSL становятся пары свойств, по одному на классе на каждом конце связи. Имена свойств отображаются на диаграмме DslDefinition как метки для ролей с каждой стороны связи. В зависимости от кратность роли тип свойства — класс на другом конце связи, либо коллекцию этого класса.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Свойства в разных концах отношения всегда являются обратная величина значения. При создании или удалении ссылки, обновляются свойства роли на обоих элементов. Следующее выражение (с использованием расширения `System.Linq`) всегда имеет значение true для отношения ParentsHaveChildren в примере:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Отношение также представленного элемента модели вызывается *ссылку*, который является экземпляром типа отношений домена. Ссылка всегда имеет один исходный элемент и один целевой элемент. Исходный и целевой элементы могут совпадать.

 Можно открыть ссылку и его свойства:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 По умолчанию для связывания каждая пара элементов модели допускается только один экземпляр отношения. Но если в определении DSL, `Allow Duplicates` флаг имеет значение true, если для связи, а затем может существовать несколько связей, и необходимо использовать `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Кроме того, существуют также другие методы для доступа к ссылкам. Пример:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Скрытые роли.** Если в определении DSL, **создается свойство** — **false** для определенной роли, затем не создается свойство, соответствующий этой роли. Тем не менее по-прежнему можно получить доступ к ссылкам и перекрестной ссылки, используя методы связи:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Наиболее часто используемые пример — <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> связи, который связывает элемент модели в фигуру, на которой он отображается на схеме:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Каталог элементов
 Доступны все элементы в хранилище, используя каталог элементов:

 `store.ElementDirectory.AllElements`

 Кроме того, существуют также методы для поиска элементов, таких как следующие:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> Доступ к сведениям о классе
 Можно получить сведения о классов, отношения и другие аспекты определения DSL. Пример:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Ниже приведены классы предка элементов модели.

-   ModelElement - все элементы и отношения являются ModelElements

-   ElementLink - все связи представляют ElementLinks

##  <a name="transaction"></a> Внести изменения в транзакции
 При каждом изменении кода программы в Store, его необходимо делать это внутри транзакции. Это относится к всех элементов модели, отношения, фигуры, схемы и их свойства. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Является наиболее удобным способом управления транзакции с `using` инструкция заключена в `try...catch` инструкции:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Можно внести любое количество изменений в рамках одной транзакции. Вы можете открыть новые транзакции внутри активной транзакции.

 Для внесения постоянных изменений, вы должны `Commit` транзакции до ее удаления. При возникновении исключения, не перехватываемое внутри транзакции, Store будут сброшены в состояние до изменения.

##  <a name="elements"></a> Создание элементов модели
 Этот пример добавляет элемент к существующей модели:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 В этом примере иллюстрирует следующие важные моменты, о создании элемента:

- Создайте новый элемент в определенной секции Store. Для элементов модели и связей, но не фигуры обычно это раздел по умолчанию.

- Сделайте его целевой объект отношения внедрения. В DslDefinition этого примера каждый пользователь должен быть целевым объектом FamilyTreeHasPeople отношения внедрения. С этой целью мы либо задайте для свойства роли FamilyTreeModel объект Person, либо добавляет пользователя к свойству роли пользователей FamilyTreeModel объекта.

- Задайте свойства нового элемента, особенно свойства, для которого `IsName` имеет значение true, если в DslDefinition. Этот флаг помечает свойство, которое служит для идентификации элемента уникально в пределах его владельцем. В этом случае свойство Name имеет флага.

- Определение DSL этот DSL должен быть загружен в Store. Если вы создаете расширения, такие как команды меню, оно обычно представлено уже true. В других случаях можно явно загрузить модель в Store, или использовать <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> загружать его. Дополнительные сведения см. в разделе [Как Открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  При создании элемента, таким образом, фигуры создается автоматически (если DSL со схемой). Он отображается в расположении, автоматически назначаемый, выполнив стандартную форму, цвет и другие функции. Если вы хотите управлять, где и как связанные фигуры отображается, см. в разделе [Создание элемента и его фигура](#merge).

##  <a name="links"></a> Создание связей
 Существуют две связи, определенные в примере определения DSL. Каждое отношение определяет *свойства роли* класса на каждом конце связи.

 Существует три способа, в которых можно создать экземпляр отношения. Каждый из этих трех методов имеет тот же эффект:

- Установите свойство исходный исполнитель роли. Пример:

  -   `familyTree.People.Add(edward);`

  -   `edward.Parents.Add(henry);`

- Свойства целевого исполнителя роли. Пример:

  -   `edward.familyTreeModel = familyTree;`

       Кратность этой роли будет `1..1`, поэтому установим значение.

  -   `henry.Children.Add(edward);`

       Кратность этой роли будет `0..*`, поэтому мы добавим в коллекцию.

- Явно создайте экземпляр связи. Пример:

  -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Последний метод полезно в том случае, если вы хотите задать свойства самого отношения.

  При создании элемента, таким образом, соединитель на схеме автоматически создается, но оно содержит фигуры по умолчанию, цвета и другие функции. Чтобы контролировать, как создается связанный соединителя, см. в разделе [Создание элемента и его фигура](#merge).

##  <a name="deleteelements"></a> Удаление элементов

Удаление элемента, вызвав `Delete()`:

`henry.Delete();`

Эта операция также удалит:

- Отношение ссылки и из элемента. Например `edward.Parents` больше не будет содержать `henry`.

- Элементы в роли, для которого `PropagatesDelete` флаг имеет значение true. Например фигура, которую отображает элемент удаляется.

По умолчанию имеет каждого отношения внедрения `PropagatesDelete` значение true, если в целевой роли. Удаление `henry` не приводит к удалению `familyTree`, но `familyTree.Delete()` удалит все `Persons`.

По умолчанию `PropagatesDelete` не относится к роли ссылочные отношения.

Может привести к правила удаления для пропуска определенной распространения при удалении объекта. Это полезно, если один элемент Подстановка для другого. Необходимо указать идентификатор GUID для одной или нескольких ролей, для которых удаление не распространяется. Идентификатор GUID можно получить из класса отношения:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Этом конкретном примере не окажет никакого влияния, так как `PropagatesDelete` — `false` для ролей в `ParentsHaveChildren` связь.)

В некоторых случаях удаление запрещена существование блокировку, в элементе или в элементе, который может удалить распространения. Можно использовать `element.CanDelete()` для проверки, может ли быть удален элемент.

##  <a name="deletelinks"></a> Удаление ссылок связи
 Вы можете удалить ссылки связи путем удаления элемента из свойства роли:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Также можно явно удалить ссылку:

 `edwardHenryLink.Delete();`

 Эти три метода действуют одинаково. Необходимо использовать один из них.

 Если роль имеет кратность 0 до 1 или 1.. 1, ему можно присвоить `null`, или на другое значение:

 `edward.FamilyTreeModel = null;` или:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Изменение порядка ссылок связи
 Ссылки определенного отношения, являются источником или предназначенные для определенного элемента модели имеют определенной последовательности. Они отображаются в порядке, в котором они были добавлены. Например Эта инструкция всегда будет давать дочерние элементы в том же порядке:

 `foreach (Person child in henry.Children) ...`

 Можно изменить порядок ссылок:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Блокировки
 Изменения можно предотвратить, блокировку. Можно задать блокировки на отдельные элементы, на секции и хранилище. Если какой-либо из этих уровней имеет блокировка, предотвращающая тип изменения, которое вы хотите сделать, может быть исключение при попытке его. Вы можете узнать, установлены ли блокировки с помощью элемента. GetLocks(), который является методом расширения, который определен в пространстве имен <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Дополнительные сведения см. в разделе [Определение политики блокировки для создания сегментов только для чтения](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Копирование и вставка
 Можно скопировать элементы или группы элементов для <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Элементы хранятся в виде сериализованного группа элементов.

 Элементы из IDataObject можно объединить в модели:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` может принимать либо `PresentationElement` или `ModelElement`. Если вы обеспечите `PresentationElement`, можно также указать позицию на целевую схему в качестве третьего параметра.

##  <a name="diagrams"></a> Переход и обновление схемы
 В DSL элемент модели домена, который представляет это концепция, например лица или музыкальной, отделен от элемента фигуры, который представляет, отображаемые на диаграмме. Элемент модели домена хранит важные свойства и отношения между основные понятия. Элемент фигуры хранит размер, положение и цвет объекта представления на диаграмме, а также макет его компонентов.

### <a name="presentation-elements"></a>Элементы представления
 ![Схема классов базовых типов фигур и элементов](../modeling/media/dslshapesandelements.png)

 В определении DSL каждый элемент вами создает класс, который является производным от одного из следующих стандартных классов.

|Тип элемента|Базовый класс|
|-|-|
|Доменный класс|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Доменная связь|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Фигура|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Соединитель|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Схема|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Обычно элемент на схеме представляет элемент модели. Обычно (но не всегда) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> представляет экземпляр класса домена и <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> представляет экземпляр отношения домена. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Связь связывает фигуру узла или связи с элементом модели, который он представляет.

 Каждая фигура, узел или ссылка относится к одной схеме. Фигура двоичной ссылки подключается двумя фигурами узлов.

 Фигуры может иметь дочерние фигуры в двух наборов. Фигуры в `NestedChildShapes` набора сводится к ограничивающего прямоугольника родительского. Фигуры в `RelativeChildShapes` списка может отображаться за пределами или частично за пределами границ родительского - например, метку или порт. Не имеет схемы `RelativeChildShapes` и не `Parent`.

###  <a name="views"></a> Переходы между фигур и элементов
 Элементы модели домена и элементы фигуры связаны с <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> связи.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Той же связи связывает связи для соединителей на схеме:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Эта связь также связывает корень модели в схему:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Чтобы получить элемент модели, представленный фигурой, используйте следующую команду:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Перемещаться по схеме
 В целом не рекомендуется для перехода между фигур и соединителей на схеме. Лучше переходить по связям в модели, перемещение между фигур и соединителей, только в том случае, когда это необходимо для работы на внешний вид схемы. Эти методы свяжите соединители фигуры на каждом конце.

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Многие фигуры состоят; они состоят из родительской фигуры и один или несколько слоев дочерних элементов. Фигуры, которые располагаются относительно другой фигуры, называются его *дочерние элементы*. При перемещении родительской фигуры, дочерние элементы перемещаются вместе с его.

 *Относительный дочерние элементы* может находиться за пределами ограничивающего прямоугольника родительской фигуры. *Вложенные* дочерние элементы появляются строго в границах родительского элемента.

 Чтобы получить верхний набор фигур на схеме, используйте следующую команду:

 `Diagram.NestedChildShapes`

 Ниже перечислены классы предка фигур и соединителей.

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> Свойства фигур и соединителей
 В большинстве случаев он необязателен для явного изменения фигуры. При изменении элементов модели правил «исправить» обновление фигур и соединителей. Дополнительные сведения см. в разделе [реагирование на события и распространение изменений](../modeling/responding-to-and-propagating-changes.md).

 Тем не менее рекомендуется внести некоторые изменения явные фигур в свойствах, которые не зависят от элементов модели. Например можно изменить эти свойства:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Определяет высоту и ширину фигуры.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -положение относительно родительской фигуры или схемы

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -набор перья и кисти, используемый для рисования фигуры или соединителя

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> — делает невидимым фигуры

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> — делает видимым после фигуры `Hide()`

###  <a name="merge"></a> Создание элемента и его фигуры

При создании элемента и связать его в дереве отношений внедрения, фигуры автоматически создается и связанные с ней. Для этого правила «исправления», которые выполняются в конце транзакции. Тем не менее фигура будет отображаться в опции автоматически назначаемый и его форму, цвет и другие функции будет иметь значения по умолчанию. Чтобы контролировать, как создается фигуры, можно использовать функцию слияния. Необходимо сначала добавить элементы, которые вы хотите добавить в ElementGroup и затем объединять группы в диаграмме.

Этот метод:

-   Задает имя, если вы назначили свойство имени элемента.

-   Обнаруживает все директивы слияния элемента, указанного в определении DSL.

В этом примере создает фигуру в позиции указателя мыши, когда пользователь дважды щелкает схему. В определении DSL в данном примере `FillColor` свойство `ExampleShape` воздействию.

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 Если указать больше одной фигуры, задайте их относительные позиции с помощью `AbsoluteBounds`.

 Можно также задать цвет и другие свойства, предоставляемого соединителей с помощью этого метода.

### <a name="use-transactions"></a>Использование транзакций
 Фигуры, соединители и схемы являются подтипами <xref:Microsoft.VisualStudio.Modeling.ModelElement> и в реальном времени в Store. Таким образом, необходимо внести изменения в них только внутри транзакции. Дополнительные сведения см. в разделе [Как Использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Просмотр документа и документа данных
 ![Схема классов стандартных типов схем](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Store секций
 При загрузке модели, соответствующие схеме загружается в то же время. Как правило модель загружается в Store.DefaultPartition и содержимое схемы загружается в другой секции. Как правило содержимое каждой секции загружается и сохраняется в виде отдельного файла.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)
- [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)
- [Практическое руководство. Обновление модели с помощью транзакций](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
