---
title: "Навигация по модели и обновление модели в программный код | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 5c7571cbb4950f91c1b69ae88241c799577f79da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Перемещение по модели и обновление модели в коде программы
Можно написать код для создания и удаления элементов модели, задавать их свойства и создания и удаления связи между элементами. Все изменения должны выполняться в рамках транзакции. Если элементы будут просмотрены в диаграмме, диаграмме будет «корректировке» автоматически в конце транзакции.  
  
## <a name="in-this-topic"></a>В этом разделе  
 [Пример определения DSL](#example)  
  
 [Навигация по модели](#navigation)  
  
 [Доступ к сведениям о классе](#metadata)  
  
 [Выполнять изменения в транзакции](#transaction)  
  
 [Создание элементов модели](#elements)  
  
 [Создание связей](#links)  
  
 [Удаление элементов](#deleteelements)  
  
 [Удаление связей](#deletelinks)  
  
 [Изменение порядка ссылки связи](#reorder)  
  
 [Блокировки](#locks)  
  
 [Копирование и вставка](#copy)  
  
 [Перехода и обновления схем](#diagrams)  
  
 [Переходы между фигур и элементов](#views)  
  
 [Свойства фигуры и соединители](#shapeProperties)  
  
 [DocView и DocData](#docdata)  
  
##  <a name="example"></a>Пример определения DSL  
 Это основная часть DslDefinition.dsl примеры в этом разделе:  
  
 ![Схема определения DSL &#45; Модель семейного дерева](../modeling/media/familyt_person.png "FamilyT_Person")  
  
 Эта модель представляет собой экземпляр этого DSL:  
  
 ![Модель1 семейного древа Тюдор](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Ссылки и пространства имен  
 Выполнение кода в этом разделе, необходимо создать ссылки:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Код будет использовать это пространство имен:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Кроме того при написании кода в другом проекте от того, в котором определен DSL, следует импортировать сборки, построенные проектом Dsl.  
  
##  <a name="navigation"></a>Навигация по модели  
  
### <a name="properties"></a>Свойства  
 Свойства домена, которые указываются в определении DSL становятся свойствами, которые можно использовать в программном коде:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Если вы хотите задать свойство, это необходимо сделать внутри [транзакции](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Если DSL определения, свойство **вид** — **вычисляемое**, задать его невозможно. Дополнительные сведения см. в разделе [вычисляемые и пользовательские свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Отношения  
 Доменная связь, которые указываются в определении DSL становятся пары свойств, один для класса на каждом конце связи. Имена свойств отображаются на диаграмме DslDefinition как метки на роли на каждой стороне связи. В зависимости от кратности роли тип свойства — класса на другом конце связи или коллекцию этого класса.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Свойства на противоположных концах связи всегда являются обратное. При создании и удалении ссылки обновляются свойства роли для обоих элементов. Следующее выражение (которая использует расширения `System.Linq`) всегда имеет значение true, если для связи ParentsHaveChildren в примере:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Связь также представлен элемент модели с именем *ссылку*, которое является экземпляром типа отношения домена. Ссылка всегда имеет один исходный элемент и один целевой элемент. Исходный и целевой элементы могут совпадать.  
  
 Вы можете использовать ссылку и его свойства:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 По умолчанию для связывания каждая пара элементов модели допускается не более одного экземпляра отношения. Но если в определении DSL `Allow Duplicates` флаг имеет значение true, если для связи, а затем может быть более одной связи и необходимо использовать `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Также существуют другие методы для доступа к ссылки. Пример:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Скрытые роли.** Если в определении DSL **создается свойство** — **false** для определенной роли, затем свойство не создаются, соответствующий этой роли. Однако по-прежнему получить доступ к ссылкам и перекрестной ссылки, с помощью методов связи:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 Наиболее часто используемые пример является <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> связи, который связывает элемент модели форма, которая отображает его на схеме:  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>Каталог элемента  
 Вы можете использовать все элементы в хранилище, используя элемент каталога:  
  
 `store.ElementDirectory.AllElements`  
  
 Существуют методы для поиска элементов, таких как следующие:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a>Доступ к сведениям о классе  
 Можно получить сведения о классов, отношения и другие аспекты определения DSL. Пример:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Ниже приведены классы предка элементов модели.  
  
-   ModelElement - все элементы и отношения, ModelElements  
  
-   ElementLink - все отношения, ElementLinks  
  
##  <a name="transaction"></a>Выполнять изменения в транзакции  
 При каждом изменении ничего в хранилище программный код должен выполняться внутри транзакции. Это применяется для всех элементов модели, связи, фигур, диаграмм и их свойства. Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.Modeling.Transaction>.  
  
 Является наиболее удобным способом управления транзакции с `using` инструкции заключены в `try...catch` инструкции:  
  
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
  
 Можно создать любое количество изменений в рамках одной транзакции. Вы можете открыть новые транзакции внутри активной транзакции.  
  
 Для внесения постоянных изменений, должны `Commit` транзакции до ее удаления. Если возникает исключение не перехватывается внутри транзакции, хранилище будут сброшены в состояние до изменения.  
  
##  <a name="elements"></a>Создание элементов модели  
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
  
 Данный пример иллюстрирует следующие основные особенности создания элемента.  
  
-   Создайте новый элемент в определенный раздел хранилища. Для элементов модели и связи, но не фигур обычно является раздела по умолчанию.  
  
-   Сделайте целевым объектом отношения внедрения. В DslDefinition в этом примере каждый пользователь должен быть целевого объекта отношения FamilyTreeHasPeople внедрения. Чтобы добиться этого, мы можно задать свойство FamilyTreeModel роль объекта Person или добавления пользователя к свойству роли пользователей FamilyTreeModel объекта.  
  
-   Задайте свойства нового элемента, особенно свойства, для которого `IsName` имеет значение true в DslDefinition. Этот флаг помечает свойство, которое служит для идентификации элемента уникально в пределах его владельца. В этом случае свойство Name имеет флага.  
  
-   Определение DSL этот DSL уже должен быть загружен в хранилище. При создании расширения, такими как команды меню, обычно это будет уже значение true. В других случаях можно явно загрузить модель в хранилище, или использовать <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> для загрузки в нее. Дополнительные сведения см. в разделе [как: открытие модели из файла в программном коде](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 При создании элемента таким образом, фигуры автоматически создается (если DSL со схемой). Оно появляется в автоматически назначаемый расположения, с формой по умолчанию, цвета и другие функции. Если вы хотите контролировать, где и как связанные формы отображается см. в разделе [Создание элемента и его фигура отображается](#merge).  
  
##  <a name="links"></a>Создание связей  
 Есть две связи, определенные в примере определения DSL. Каждая связь определяет *свойство роли* класса на каждом конце связи.  
  
 Существует три способа, в которых можно создать экземпляр отношения. Каждый из этих трех методов имеет тот же эффект.  
  
-   Задайте для свойства исполнителя роли источника. Пример:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   Свойства целевого исполнителя роли. Пример:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         Кратность этой роли `1..1`, поэтому мы присвоить это значение.  
  
    -   `henry.Children.Add(edward);`  
  
         Кратность этой роли `0..*`, поэтому мы добавить в коллекцию.  
  
-   Явно создайте экземпляр связи. Пример:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 Последний метод полезно использовать для задания свойств сама связь.  
  
 При создании элемента таким образом, автоматически создается соединитель на диаграмме, но он имеет форму по умолчанию, цвета и другие возможности. Чтобы контролировать, как создается связанный соединитель, см. [Создание элемента и его фигура отображается](#merge).  
  
##  <a name="deleteelements"></a>Удаление элементов  
 Удаление элемента, вызвав `Delete()`:  
  
 `henry.Delete();`  
  
 Эта операция также удалит:  
  
-   Ссылок на связи в и из элемента. Например `edward.Parents` больше не будет содержать `henry`.  
  
-   Элементы в роли, для которой `PropagatesDelete` флаг имеет значение true. Например фигуру, отображение элемента будут удалены.  
  
 По умолчанию имеет все связи внедренные `PropagatesDelete` значение true, если в целевой роли. Удаление `henry` не приводит к удалению `familyTree`, но `familyTree.Delete()` , удаление всех `Persons`. Дополнительные сведения см. в разделе [Настройка поведения удаления](../modeling/customizing-deletion-behavior.md).  
  
 По умолчанию `PropagatesDelete` не относится к роли ссылочные связи.  
  
 Может вызвать правила удаления для пропуска определенной распространения при удалении объекта. Это полезно, если один элемент замены для другого. Можно указать идентификатор GUID для одной или нескольких ролей, которые удаления не будет распространяться. Идентификатор GUID можно получить из класса отношения:  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (Данном конкретном примере окажет никакого влияния, так как `PropagatesDelete` — `false` для ролей `ParentsHaveChildren` связь.)  
  
 В некоторых случаях удаление запрещена существование блокировка, на элемент или элемент, который может удалить распространения. Можно использовать `element.CanDelete()` для проверки, может ли быть удален элемент.  
  
##  <a name="deletelinks"></a>Удаление связей  
 Связь связи можно удалить, удалив элемент из свойства роли:  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Также можно явно удалить ссылку:  
  
 `edwardHenryLink.Delete();`  
  
 Эти три метода действуют одинаково. Необходимо использовать один из них.  
  
 Если роль имеет кратность 0 до 1 или 1.. 1, можно задать значение `null`, или на другое значение:  
  
 `edward.FamilyTreeModel = null;`или:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a>Перегруппировка ссылки связи  
 По ссылкам определенной связи, источником или адресованный элемент конкретной модели имеют определенной последовательности. Они отображаются в порядке, в котором они были добавлены. Например Эта инструкция может давать дочерние элементы в том же порядке:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Можно изменить порядок ссылок:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a>Блокировки  
 Изменения могут быть недоступны блокировкой. Блокировки можно задать отдельные элементы, разделы и хранилище. Если любой из этих уровней блокировка, предотвращающая тип изменения, необходимо сделать, может быть исключение при попытке его. Вы можете узнать, установлены ли блокировки с помощью элемента. GetLocks(), который является методом расширения, который определен в пространстве имен <xref:Microsoft.VisualStudio.Modeling.Immutability>.  
  
 Дополнительные сведения см. в разделе [Определение политики блокировки для создания сегментов только для чтения](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="copy"></a>Копирование и вставка  
 Можно копировать элементы или группы элементов, которые требуется <xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Элементы хранятся в виде сериализованный группы элементов.  
  
 Можно объединять элементы из IDataObject в модели:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`может принимать либо `PresentationElement` или `ModelElement`. Если вы обеспечите такую `PresentationElement`, можно также указать позицию в целевой диаграмме в качестве третьего параметра.  
  
##  <a name="diagrams"></a>Перехода и обновления схем  
 В доменный язык DSL элемента модели домена, который представляет понятие, например пользователя или песню, отделен от элемент фигуры, который представляет содержимое, отображаемое на диаграмме. Элемент модели домена хранит важные свойства и связи понятий. Элемент фигуры сохраняет размер, положение и цвет объекта представления на диаграмме, а макет ее компонентов.  
  
### <a name="presentation-elements"></a>Элементы представления  
 ![Схема классов базовых типов фигур и элементов](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 В определении DSL каждого элемента, который указывается создает класс, который является производным от одного из следующих стандартных классов.  
  
|Тип элемента|Базовый класс|  
|---------------------|----------------|  
|Класс домена|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Доменная связь|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Фигура|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Соединитель|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Схема|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Обычно элемент на схеме представляет элемент модели. Обычно (но не всегда) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> представляет экземпляр класса домена и <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> представляет экземпляр связи домена. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Связь связывает фигуры узла или ссылки на элемент модели, который он представляет.  
  
 Каждый узел или ссылка фигуры принадлежит к одной схеме. Фигура бинарной связи соединяет два узла фигуры.  
  
 Фигуры могут иметь дочерние фигуры в двух наборов. Фигуры в `NestedChildShapes` набор сводится к ограничивающего прямоугольника родительского элемента. Фигуры в `RelativeChildShapes` отображения списка снаружи или частично вне границ родительского - например, метки или порт. Не содержит схему `RelativeChildShapes` и не `Parent`.  
  
###  <a name="views"></a>Переходы между фигур и элементов  
 Элементы модели домена и элементы фигуры связываются с помощью <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> связи.  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 Той же связи ссылки связи соединительные линии на диаграмме:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Эта связь также связывает корень модели к диаграмме:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Чтобы получить элемент модели, представленной фигуры, используйте следующую команду:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Перемещаться по схеме  
 Обычно не рекомендуется для перехода между фигуры и соединители на диаграмме. Рекомендуется для перехода по связям в модели, перемещение между фигуры и соединители, только в том случае, когда это необходимо для работы на внешний вид диаграммы. Эти методы ссылки соединители фигур на каждом конце:  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Многие фигуры являются составными; они состоят из родительской фигуры и один или несколько уровней дочерних элементов. Фигуры, которые имеют относительно другую форму, называются его *дочерних*. При перемещении родительской фигуры, дочерние элементы перемещаются вместе с его.  
  
 *Дочерние элементы относительный* может отображаться за пределами ограничивающего прямоугольника родительской фигуры. *Вложенные* дочерние элементы появляются строго в границах родительского элемента.  
  
 Чтобы получить верхний набор фигур на схеме, используйте следующую команду:  
  
 `Diagram.NestedChildShapes`  
  
 Ниже приведены классы предка фигуры и соединители:  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="shapeProperties"></a>Свойства фигуры и соединители  
 В большинстве случаев не требуется освободить явного изменения к фигурам. При изменении элементов модели «исправьте» правила обновления фигуры и соединители. Дополнительные сведения см. в разделе [распространение изменений и реагирование на](../modeling/responding-to-and-propagating-changes.md).  
  
 Тем не менее рекомендуется внести некоторые изменения явную фигур в свойствах, которые не зависят от элементов модели. Например можно изменить эти свойства:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-Определяет высоту и ширину фигуры.  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-позиции относительно Родительская фигура или схема  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-набор перья и кисти, используемую для рисования фигуры или соединителя  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>— делает невидимым фигуры  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>— делает видимой после фигуры`Hide()`  
  
###  <a name="merge"></a>Создание элемента и его фигуры  
 При создании элемента и связать его в дерево внедрения связей, фигуры автоматически создается и связанные с ним. Это делается путем правила «исправление», которые выполняются в конце транзакции. Тем не менее форма будет отображаться в расположении, автоматически назначается и его фигура, цвета и другие возможности будут иметь значения по умолчанию. Чтобы управлять созданием фигуры, можно использовать функцию слияния. Необходимо сначала добавить элементы, которые требуется добавить в ElementGroup и объединять группы в диаграмме.  
  
 Этот метод:  
  
-   Задает имя, если вы назначили свойство имени элемента.  
  
-   Обнаруживает все элемент слияния директивы, который указан в определении DSL.  
  
 Этот пример создает фигуру в положении указателя, при двойном щелчке в схеме. В определении DSL для данного образца `FillColor` свойство `ExampleShape` предоставленный.  
  
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
  
 Если указать более одной формы, задать их относительные позиции с помощью `AbsoluteBounds`.  
  
 Можно также задать цвет и других свойств соединителей, с помощью этого метода.  
  
### <a name="use-transactions"></a>Использование транзакций  
 Фигуры, соединители и схемы являются подтипами <xref:Microsoft.VisualStudio.Modeling.ModelElement> и в активном состоянии в хранилище. Таким образом, необходимо внести изменения в их только внутри транзакции. Дополнительные сведения см. в разделе [как: использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="docdata"></a>Представление документов и данных документа  
 ![Схема классов стандартных типов схем](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Хранилище секций  
 При загрузке модели, соответствующие схеме загружается в то же время. Как правило модель загружается в Store.DefaultPartition и содержимое схемы загружается в другой секции. Как правило содержимое каждой секции загружается и сохраняется в отдельный файл.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Проверка доменного языка](../modeling/validation-in-a-domain-specific-language.md)   
 [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Как: использовать транзакции для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
