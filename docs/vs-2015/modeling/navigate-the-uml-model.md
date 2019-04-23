---
title: Навигация по модели UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b61492d992d37d7377e73185202bfbdd97063195
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116671"
---
# <a name="navigate-the-uml-model"></a>Навигация по модели UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе представлены основные типы модели UML.  
  
## <a name="the-model-elements-model-and-model-store"></a>Элементы модели, модель и ее хранилище  
 Типы, определенные в сборке **Microsoft.VisualStudio.Uml.Interfaces.dll** соответствуют типам, определенным в [спецификации UML версии 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 Типы в спецификации UML реализуются в Visual Studio как интерфейсы. Перед именем каждого типа добавляется буква "I". Примеры: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 Все типы, кроме IElement, наследуют свойства от одного или нескольких супертипов.  
  
- Краткое описание типов модели, см. в разделе [типы элементов модели UML](../modeling/uml-model-element-types.md).  
  
- Полные сведения об API см. в разделе [Справочник по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>Отношения  
 Свойства и связи, определенные в спецификации UML, реализуются в виде свойств .NET.  
  
 Большинство связей поддерживают переходы в обоих направлениях. Связь соответствует паре свойств: по одному свойству на каждом конце. Например, свойства `IElement.Owner` и `IElement.OwnedElements` соответствуют двум концам связи. Поэтому значением этого выражения всегда будет true.  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 Многие связи, например IAssociation, представляются также с помощью объекта, у которого могут быть свои собственные свойства.  
  
 При удалении элемента из модели все связи, в которых он был задействован, автоматически удаляются с обновлением свойства на другом конце.  
  
 Если в спецификации UML для свойства задается кратность 0..1, оно может иметь значение `null`. Максимальное значение кратности больше 1 означает, что свойство .NET имеет тип: `IEnumerable<`*Тип*`>`.  
  
 Дополнительные сведения о просмотре связей см. в разделе [переход по отношениям с помощью UML API](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Дерево собственности  
 В модели содержится дерево объектов <xref:Microsoft.VisualStudio.Uml.Classes.IElement>. У каждого элемента есть свойства `OwnedElements` и `Owner`.  
  
 В большинстве случаев на свойства `Owner` и `OwnedElements` также ссылаются другие свойства с более конкретными именами. Например, каждая операция UML принадлежит классу UML. Поэтому у типа <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> есть свойство с именем <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A>. В каждом объекте <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> его значение равно `Class == Owner`.  
  
 Самый верхний элемент в дереве, у которого нет владельца, — <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. Тип IModel содержится в объекте <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, в котором он является свойством <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Каждый элемент модели создается с владельцем. Дополнительные сведения см. в разделе [создание элементов и отношений в моделях UML](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Схема классов: Модель, схема, фигура и элемент](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Фигуры и схемы  
 В модели UML элементы можно отобразить на схемах. На разных типах схем могут отображаться различные подтипы IElement.  
  
 В некоторых случаях элемент может отображаться на нескольких схемах. Например, у элемента IUseCase может быть несколько фигур IShape, которые могут отображаться на одной или нескольких схемах.  
  
 Фигуры упорядочиваются в виде дерева. Края дерева представлены свойствами ParentShape и ChildShapes. Схемы — это единственные фигуры, у которых нет родительских объектов. Фигуры на поверхности схемы состоят из более мелких частей. Например, у фигуры класса есть секции для атрибутов и операций.  
  
 Дополнительные сведения о фигурах см. в разделе [отображение модели UML на схемах](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Доступ к модели в расширениях  
 В расширениях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], определенных в качестве компонентов MEF, можно объявить свойства, импортирующие данные из контекста, в котором выполняется расширение.  
  
|Тип атрибута|К чему предоставляется доступ|Дополнительные сведения|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (в Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Схема текущего фокуса.|[Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (в Microsoft.VisualStudio.Modeling.Sdk.[версия].dll)|Позволяет группировать изменения в транзакции.|[Связывание обновлений модели UML с использованием транзакций](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (в Microsoft.VisualStudio.Shell.Immutable.[версия].dll)|Основной экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Здесь можно получить доступ к файлам, проектам и другим элементам.|[Открытие модели UML с помощью API Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Получение контекста  
 Объявите один или оба приведенных ниже интерфейса внутри класса расширения.  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Платформа Managed Extensibility Framework (MEF) свяжет их с определениями, из которых можно получить текущую схему, хранилище моделей, корневой объект и т. д.  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Получение текущего выделения  
  
```  
// All selected shapes and their elements  
foreach (IShape shape in diagram.SelectedShapes)  
{    
   IDiagram selectedDiagram = shape as IDiagram;  
   if (selectedDiagram != null)  
   { // no shape selected - user right-clicked the diagram  
     ... Context.CurrentDiagram ...  
   }  
   else  
   {  
     IElement selectedElement = shape.Element;  
   ...}  
// All selected shapes that display a specfic type of element  
foreach (IShape<IInterface> in   
   diagram.GetSelectedShapes<IInterface>())   
{...}  
```  
  
## <a name="accessing-another-model-or-diagrams"></a>Доступ к другой модели или схемам  
 Можно выполнить следующие действия:   
  
- Используйте шину модели [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания ссылок между элементами в разных моделях. Дополнительные сведения см. в разделе [интеграция моделей UML с другими моделями и средствами](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
- Загружайте проект и схемы моделирования в режиме только для чтения, не делая их видимыми в пользовательском интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [чтение модели UML в программном коде](../modeling/read-a-uml-model-in-program-code.md).  
  
- Откройте проект моделирования и его схемы в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и начните работу с содержимым. Дополнительные сведения см. в разделе [Открытие модели UML с помощью Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)
