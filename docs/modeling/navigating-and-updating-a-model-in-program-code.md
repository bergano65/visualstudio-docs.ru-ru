---
title: "Перемещение и обновление модели в программный код | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: f17f676025a19efb09184b7a49645986723cb29f
ms.lasthandoff: 02/22/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Перемещение по модели и обновление модели в коде программы
Можно написать код для создания и удаления элементов модели, задайте их свойства, создавать и удалять связи между элементами. Все изменения должны выполняться в рамках транзакции. Если элементы можно просмотреть на диаграмме, диаграмме «фиксируется» автоматически в конце транзакции.  
  
## <a name="in-this-topic"></a>В этом разделе  
 [Пример определения DSL](#example)  
  
 [Перемещение по модели](#navigation)  
  
 [Доступ к сведениям о классе](#metadata)  
  
 [Выполнять изменения в транзакции](#transaction)  
  
 [Создание элементов модели](#elements)  
  
 [Создание связей](#links)  
  
 [Удаление элементов](#deleteelements)  
  
 [Удаление связей](#deletelinks)  
  
 [Изменение порядка ссылок связи](#reorder)  
  
 [Блокировки](#locks)  
  
 [Копирование и вставка](#copy)  
  
 [Перемещение и обновление схем](#diagrams)  
  
 [Переходы между фигур и элементов](#views)  
  
 [Свойства фигур и соединителей](#shapeProperties)  
  
 [DocView и DocData](#docdata)  
  
##  <a name="a-nameexamplea-an-example-dsl-definition"></a><a name="example"></a>Пример определения DSL  
 Это основная часть DslDefinition.dsl в примерах в этом разделе:  
  
 ![Схема определения DSL — модель семейного дерева](~/docs/modeling/media/familyt_person.png "FamilyT_Person")  
  
 Эта модель является экземпляром данного DSL:  
  
 ![Модель1 семейного древа Тюдор](~/docs/modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Ссылки и пространства имен  
 Выполнение кода в этом разделе, необходимо создать ссылки:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Код будет использовать это пространство имен:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Кроме того при написании кода в другом проекте от той, в которой определен DSL, следует импортировать сборку, созданного проекта Dsl.  
  
##  <a name="a-namenavigationa-navigating-the-model"></a><a name="navigation"></a>Перемещение по модели  
  
### <a name="properties"></a>Свойства  
 Свойства домена, заданные в определении DSL становятся свойствами, которые доступны в программном коде:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Если вы хотите задать свойство, это необходимо сделать в [транзакции](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Если в определении DSL, свойство **вид** — **вычисляемое**, нельзя задать шаблон. Дополнительные сведения см. в разделе [вычисляемые и пользовательские свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Отношения  
 Доменные связи, определенные в определении DSL становятся пары свойств, по одному на классе на каждом конце связи. Имена свойств отображаются в схеме DslDefinition как метки на роли на каждой стороне связи. В зависимости от кратности роли тип свойства — класса на другом конце связи или коллекцию этого класса.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Свойства в разных концах отношения всегда являются обратное. При создании и удалении ссылки обновляются свойства роли на обоих элементов. Следующее выражение (которая использует расширения `System.Linq`) всегда имеет значение true для отношения ParentsHaveChildren в примере:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Связь также представлен элемент модели с именем *ссылки*, который является экземпляром типа отношения домена. Ссылка всегда имеет один источник и один целевой элемент. Исходный и целевой элементы могут совпадать.  
  
 Можно открыть ссылку и его свойства:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 По умолчанию не более одного экземпляра отношения разрешается связь каждая пара элементов модели. Но если в определении DSL `Allow Duplicates` флаг имеет значение true, если для связи, а затем может быть более одной связи и необходимо использовать `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Существуют также другие методы доступа к ссылки. Например:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Скрытые роли.** Если в определении DSL **создается свойство** — **false** для определенной роли, затем свойство не создается, соответствующий этой роли. Однако по-прежнему получить доступ к ссылкам и перекрестной ссылки, с помощью методов связи:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 Наиболее часто используемые пример <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>связь, которая связывает элемент модели форма, которая отображает его на схеме:</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>Каталог элемента  
 Можно получить все элементы в хранилище, используя элемент каталога:  
  
 `store.ElementDirectory.AllElements`  
  
 Существуют также методы для поиска элементов, таких как следующие:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="a-namemetadataa-accessing-class-information"></a><a name="metadata"></a>Доступ к сведениям о классе  
 Можно получить сведения о классов, отношения и другие аспекты определения DSL. Пример:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Ниже приведены классы предка элементов модели.  
  
-   ModelElement - все элементы и отношения, ModelElements  
  
-   ElementLink - все связи представляют собой ElementLinks  
  
##  <a name="a-nametransactiona-perform-changes-inside-a-transaction"></a><a name="transaction"></a>Выполнять изменения в транзакции  
 Каждый раз, когда программный код меняет все в магазине, она должна будет работать внутри транзакции. Это применяется для всех элементов модели, отношения, фигуры, схемы и их свойства. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Modeling.Transaction>.</xref:Microsoft.VisualStudio.Modeling.Transaction>  
  
 Является наиболее удобный способ управления транзакции с `using` заключена в `try...catch` инструкции:  
  
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
  
 Можно выполнить любое количество изменений в рамках одной транзакции. Можно открыть новые транзакции внутри активной транзакции.  
  
 Для внесения постоянных изменений, должны `Commit` транзакции до ее удаления. Если возникает исключение не перехватывается внутри транзакции, хранилище будут сброшены в состояние до изменения.  
  
##  <a name="a-nameelementsa-creating-model-elements"></a><a name="elements"></a>Создание элементов модели  
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
  
 Данный пример иллюстрирует следующие важные особенности создания элемента.  
  
-   Создайте новый элемент в отдельной секции хранилища. Для элементов модели и связи, но не формы обычно это раздела по умолчанию.  
  
-   Сделайте целевой объект отношения внедрения. В DslDefinition в этом примере каждый пользователь должен быть целевым внедрения связи FamilyTreeHasPeople. Для этого мы либо задать свойство FamilyTreeModel роли объекта Person, либо добавить пользователя в свойство роли пользователей объекта FamilyTreeModel.  
  
-   Задайте свойства нового элемента, особенно свойства, для которого `IsName` имеет значение true, если в DslDefinition. Этот флаг указывает свойство, которое служит для идентификации элемента уникально в пределах его владельца. В этом случае свойство Name имеет флага.  
  
-   Определение DSL этот DSL уже должен быть загружен в хранилище. При создании расширения, например, команда меню, обычно это будет уже true. В других случаях можно явно загрузить модель в хранилище или использовать <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>для загрузки его.</xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> Дополнительные сведения см. в разделе [Практическое руководство: открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 При создании элемента таким образом, фигуры автоматически создается (если DSL со схемой). Оно появляется в адрес автоматически назначенный с формой по умолчанию, цвета и другие функции. Если вы хотите контролировать, где и как связанные фигуры появится см. в разделе [Создание элемента и его фигура](#merge).  
  
##  <a name="a-namelinksa-creating-relationship-links"></a><a name="links"></a>Создание связей  
 Имеются два отношения, определенные в примере определения DSL. Каждое отношение определяет *роли свойство* класса на каждом конце связи.  
  
 Существует три способа, в которых можно создать экземпляр связи. Каждый из этих трех методов имеет тот же эффект:  
  
-   Задайте для свойства исходный исполнитель роли. Пример:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Свойства целевого исполнителя роли. Пример:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         Кратность этой роли является `1..1`, поэтому установим значение.  
  
    -   `henry.Children.Add(edward);`  
  
         Кратность этой роли является `0..*`, поэтому мы добавляем в коллекцию.  
  
-   Явным образом создавать экземпляр связи. Например:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 Последний метод является полезным, если вы хотите задать свойства самого отношения.  
  
 При создании элемента таким образом, соединитель на схеме автоматически создается, но он имеет форму по умолчанию, цвета и другие функции. Для управления как создается связанный соединитель см [Создание элемента и его фигура](#merge).  
  
##  <a name="a-namedeleteelementsa-deleting-elements"></a><a name="deleteelements"></a>Удаление элементов  
 Удаление элемента путем вызова `Delete()`:  
  
 `henry.Delete();`  
  
 Эта операция также удаляет:  
  
-   Связи отношений в и из элемента. Например `edward.Parents` больше не будет содержать `henry`.  
  
-   Элементы роли, для которой `PropagatesDelete` флаг имеет значение true. Например фигуру, которая отображает элемент удаляется.  
  
 По умолчанию имеет каждого отношения внедрения `PropagatesDelete` значение true, в целевой роли. Удаление `henry` не приводит к удалению `familyTree`, но `familyTree.Delete()` , удаление всех `Persons`. Дополнительные сведения см. в разделе [Настройка функции удаления](../modeling/customizing-deletion-behavior.md).  
  
 По умолчанию `PropagatesDelete` не относится к роли ссылочные отношения.  
  
 Можно вызвать правила удаления исключить определенные распространение при удалении объекта. Это полезно, если один элемент заменив для другого. Необходимо указать одну или несколько ролей, которые удаления не удалось распространить идентификатор GUID. Идентификатор GUID можно получить из класса отношения:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (Данном примере будет иметь никакого влияния, поскольку `PropagatesDelete` — `false` для роли `ParentsHaveChildren` связи.)  
  
 В некоторых случаях удаление запрещена существование блокировку на элемент или элемент, который будет удален, распространение. Можно использовать `element.CanDelete()` для проверки, может ли быть удален элемент.  
  
##  <a name="a-namedeletelinksa-deleting-relationship-links"></a><a name="deletelinks"></a>Удаление связей  
 Ссылки связи можно удалить, удалив элемент из свойства роли.  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Также можно явно удалить ссылку:  
  
 `edwardHenryLink.Delete();`  
  
 Эти три метода действуют одинаково. Необходимо использовать один из них.  
  
 Если роль имеет кратность 0 до 1 или 1.. 1, ему можно присвоить `null`, или на другое значение:  
  
 `edward.FamilyTreeModel = null;`или:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="a-namereordera-re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a>Изменение порядка ссылок связи  
 Ссылки из определенной связи, являющиеся источником или предназначенные элемент конкретной модели имеют определенной последовательности. Они отображаются в порядке, в котором они были добавлены. Например Эта инструкция может давать дочерние элементы в том же порядке:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Можно изменить порядок ссылок:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="a-namelocksa-locks"></a><a name="locks"></a>Блокировки  
 Изменения могут быть недоступны блокировкой. Можно задать блокировки на отдельные элементы, разделы и хранилище. Если любой из этих уровней блокировка, предотвращающая тип изменения, что нужно сделать, может возникнуть исключение при попытке его. Вы можете узнать, установлены ли блокировки с помощью элемента. GetLocks(), который является методом расширения, который определен в пространстве имен <xref:Microsoft.VisualStudio.Modeling.Immutability>.</xref:Microsoft.VisualStudio.Modeling.Immutability>  
  
 Дополнительные сведения см. в разделе [Определение политики блокировки для создания сегментов только для чтения](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="a-namecopya-copy-and-paste"></a><a name="copy"></a>Копирование и вставка  
 Можно скопировать элементы или группы элементов <xref:System.Windows.Forms.IDataObject>:</xref:System.Windows.Forms.IDataObject>  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Элементы сохраняются как сериализованный элемент группы.  
  
 В модели можно объединять элементы из IDataObject:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`можно либо принять `PresentationElement` или `ModelElement`. Если вы обеспечите `PresentationElement`, можно также указать позицию на целевую схему как третий параметр.  
  
##  <a name="a-namediagramsa-navigating-and-updating-diagrams"></a><a name="diagrams"></a>Перемещение и обновление схем  
 В DSL элемент модели домена, который представляет концепции, например человека или музыкальной записи, отдельно от элемента фигуры, который представляет отображаемые на диаграмме. Элемент модели домена хранит важные свойства и отношения понятий. Элемент фигуры сохраняет размер, положение и цвет объекта представления на диаграмме, а макет ее компонентов.  
  
### <a name="presentation-elements"></a>Представление элементов  
 ![Схема классов базовых типов фигур и элементов](~/docs/modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 В определении DSL каждого элемента, который указывается создает класс, производный от одного из следующих стандартных классов.  
  
|Тип элемента|Базовый класс|  
|---------------------|----------------|  
|Класс домена|<xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Доменная связь|<xref:Microsoft.VisualStudio.Modeling.ElementLink></xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Фигура|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Соединитель|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Схема|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Обычно элемент на схеме представляет элемент модели. Обычно (но не всегда) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>представляет экземпляр класса домена и <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>представляет экземпляр отношения домена.</xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> </xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>Связь связывает фигуры узла или ссылки на элемент модели, который он представляет.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 Каждая фигура узла или связи принадлежит одной схеме. Фигура бинарной связи соединяет два узла фигуры.  
  
 Фигуры могут иметь дочерние формы в двух наборов. Фигуры в `NestedChildShapes` набора сводится к ограничивающего прямоугольника родительского элемента. Фигуры в `RelativeChildShapes` списка могут отображаться за пределами или частично за пределами границ родительского — например, метки или порт. Не имеет схемы `RelativeChildShapes` и не `Parent`.  
  
###  <a name="a-nameviewsa-navigating-between-shapes-and-elements"></a><a name="views"></a>Переходы между фигур и элементов  
 Элементы модели домена и элементы фигуры связаны с <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>связь.</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
```c#  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 Отношения ссылки той же связи соединительные линии на диаграмме:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Это отношение также связывает корень модели в схему:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Чтобы получить элемент модели, представленный фигурой, используйте следующую команду:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Перемещаться по схеме  
 В целом не рекомендуется, чтобы переходить между фигур и соединителей на схеме. Переход по связям в модели, перемещение между фигур и соединителей, только в том случае, если это необходимо для работы на внешний вид схемы лучше. Эти методы свяжите соединители фигур на каждом конце.  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Многие фигуры являются составляющими; они состоят из родительской фигуры и один или несколько слоев дочерних элементов. Фигуры, которые расположены по отношению к другой фигуры, называются его *дочерних*. При перемещении родительской фигуры, потомки перемещается вместе с ним.  
  
 *Относительный дочерних* может находиться за пределами ограничивающего прямоугольника родительской фигуры. *Вложенные* дочерние элементы появляются строго в границах родительского элемента.  
  
 Чтобы получить верхний набор фигур на схеме, используйте следующую команду:  
  
 `Diagram.NestedChildShapes`  
  
 Перечислены классы предка фигур и соединителей.  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="a-nameshapepropertiesa-properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a>Свойства фигур и соединителей  
 В большинстве случаев не требуется для явного изменения фигуры. При изменении элементов модели правил «исправить» обновление фигур и соединителей. Дополнительные сведения см. в разделе [распространение изменений и реагирование на](../modeling/responding-to-and-propagating-changes.md).  
  
 Однако имеет смысл внести некоторые изменения явную фигур в свойствах, которые не зависят от элементов модели. Например можно изменить эти свойства:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-Определяет высоту и ширину фигуры.</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-расположение относительно Родительская фигура или схема</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-Набор перьев и кистей, используемый для рисования фигуры или соединителя</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-делает невидимым фигуры</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-делает видимой после фигуры`Hide()`</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>  
  
###  <a name="a-namemergea-creating-an-element-and-its-shape"></a><a name="merge"></a>Создание элемента и его фигура  
 При создании элемента и связать его в дерево отношений внедрения, фигуры автоматически создается и связанные с ним. Это делается путем «исправления» правила, которые выполняются в конце транзакции. Тем не менее фигуры будут отображаться в папке автоматически назначается, и его фигура, цвет и другие функции будет иметь значения по умолчанию. Позволяет указать, как создавать фигуры, можно использовать функцию слияния. Необходимо сначала добавить элементы, которые требуется добавить в ElementGroup и затем объединять группы в диаграмме.  
  
 Этот метод:  
  
-   Задает имя, если вы назначили свойство имени элемента.  
  
-   Обнаруживает все директивы слияния элемента, заданного в определении DSL.  
  
 Этот пример создает фигуры в положении указателя, при двойном щелчке диаграммы. В определении доменного языка для данного образца `FillColor` свойства `ExampleShape` подвергшегося.  
  
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
  
 Если имеется более одной фигуры, задайте их относительные позиции с помощью `AbsoluteBounds`.  
  
 Можно также задать цвет и другие свойства, предоставленные соединителей с помощью этого метода.  
  
### <a name="use-transactions"></a>Использование транзакций  
 Фигуры, соединители и схемы являются подтипами <xref:Microsoft.VisualStudio.Modeling.ModelElement>и live в хранилище.</xref:Microsoft.VisualStudio.Modeling.ModelElement> Таким образом, необходимо внести изменения в них только внутри транзакции. Дополнительные сведения см. в разделе [Практическое руководство: использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="a-namedocdataa-document-view-and-document-data"></a><a name="docdata"></a>Представление документов и данных документа  
 ![Схема классов стандартных типов схем](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Хранилище секций  
 При загрузке модели сопутствующий схемы загружается в то же время. Как правило модель загружается в Store.DefaultPartition и содержимое схемы загружается в другой секции. Как правило содержимое каждого раздела загружается и сохраняется в отдельном файле.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)   
 [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Практическое руководство: использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)

