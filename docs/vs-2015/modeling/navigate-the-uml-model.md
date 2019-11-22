---
title: Navigate the UML model | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23f87c81e43b2dfafb1c9c78c3135faff809bb9f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289859"
---
# <a name="navigate-the-uml-model"></a>Навигация по модели UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе представлены основные типы модели UML.

## <a name="the-model-elements-model-and-model-store"></a>Элементы модели, модель и ее хранилище
 The types defined in the assembly **Microsoft.VisualStudio.Uml.Interfaces.dll** correspond to the types defined in the [UML Specification, version 2.1.2](https://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).

 Типы в спецификации UML реализуются в Visual Studio как интерфейсы. Перед именем каждого типа добавляется буква "I". For example: [IElement](/previous-versions/dd516035(v=vs.140)), [IClass](/previous-versions/dd523539%28v%3dvs.140%29), [IOperation](/previous-versions/dd481186(v=vs.140)).

 Все типы, кроме IElement, наследуют свойства от одного или нескольких супертипов.

- For a summary of the model types, see [UML model element types](../modeling/uml-model-element-types.md).

- For full details of the API, see [API Reference for UML Modeling Extensibility](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>Отношения
 Свойства и связи, определенные в спецификации UML, реализуются в виде свойств .NET.

 Большинство связей поддерживают переходы в обоих направлениях. Связь соответствует паре свойств: по одному свойству на каждом конце. Например, свойства `IElement.Owner` и `IElement.OwnedElements` соответствуют двум концам связи. Поэтому значением этого выражения всегда будет true.

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 Многие связи, например IAssociation, представляются также с помощью объекта, у которого могут быть свои собственные свойства.

 При удалении элемента из модели все связи, в которых он был задействован, автоматически удаляются с обновлением свойства на другом конце.

 Если в спецификации UML для свойства задается кратность 0..1, оно может иметь значение `null`. A multiplicity with maximum greater than 1 means that the .NET property has the type: `IEnumerable<`*Type*`>`.

 For more information about traversing relationships, see [Navigate relationships with the UML API](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>Дерево собственности
 A model contains a tree of [IElement](/previous-versions/dd516035(v=vs.140)) objects. У каждого элемента есть свойства `OwnedElements` и `Owner`.

 В большинстве случаев на свойства `Owner` и `OwnedElements` также ссылаются другие свойства с более конкретными именами. Например, каждая операция UML принадлежит классу UML. Therefore [IOperation](/previous-versions/dd481186(v=vs.140)) has a property named [IOperation.Class](/previous-versions/dd473473%28v%3dvs.140%29), and in every [IOperation](/previous-versions/dd481186(v=vs.140)) object, `Class == Owner`.

 The topmost element of the tree, which has no Owner, is an `AuxiliaryConstructs.IModel`. The IModel is contained within a `IModelStore`, in which it is the [IModelStore.Root](/previous-versions/ee789368(v=vs.140)).

 Каждый элемент модели создается с владельцем. For more information, see [Create elements and relationships in UML models](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Схема классов: модель, схема, фигура и элемент](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Фигуры и схемы
 В модели UML элементы можно отобразить на схемах. На разных типах схем могут отображаться различные подтипы IElement.

 В некоторых случаях элемент может отображаться на нескольких схемах. Например, у элемента IUseCase может быть несколько фигур IShape, которые могут отображаться на одной или нескольких схемах.

 Фигуры упорядочиваются в виде дерева. Края дерева представлены свойствами ParentShape и ChildShapes. Схемы — это единственные фигуры, у которых нет родительских объектов. Фигуры на поверхности схемы состоят из более мелких частей. Например, у фигуры класса есть секции для атрибутов и операций.

 For more information about shapes, see [Display a UML model on diagrams](../modeling/display-a-uml-model-on-diagrams.md).

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
 Можно выполнить следующие действия.

- Используйте шину модели [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания ссылок между элементами в разных моделях. For more information, see [Integrate UML models with other models and tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Загружайте проект и схемы моделирования в режиме только для чтения, не делая их видимыми в пользовательском интерфейсе [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. For more information, see [Read a UML model in program code](../modeling/read-a-uml-model-in-program-code.md).

- Откройте проект моделирования и его схемы в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и начните работу с содержимым. For more information, see [Open a UML model by using the Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>См. также

- [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)
- [Программирование с UML API](../modeling/programming-with-the-uml-api.md)
