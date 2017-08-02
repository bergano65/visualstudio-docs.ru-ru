---
title: "Переход и обновление моделей слоев в коде программы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 626fc2b217285ae0c79dbd57f925281e10a0efbb
ms.lasthandoff: 02/22/2017

---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Перемещение по моделям слоев в коде программы и их обновление
В этом разделе рассматриваются элементы и отношения в моделях слоев, к которым можно перейти и которые можно обновить с помощью программного кода. Дополнительные сведения о схемах зависимостей с точки зрения пользователя см. в разделе [схемы зависимостей: справочник](../modeling/layer-diagrams-reference.md) и [схемы зависимостей: рекомендации по](../modeling/layer-diagrams-guidelines.md).  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer>Модели, описанные в этом разделе является интерфейсом более общей <xref:Microsoft.VisualStudio.GraphModel>модели.</xref:Microsoft.VisualStudio.GraphModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> При создании [меню расширения команды или жеста](../modeling/add-commands-and-gestures-to-layer-diagrams.md), используйте `Layer` модели. При создании [расширения проверки слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), проще использовать `GraphModel`.  
  
## <a name="transactions"></a>Транзакции  
 При обновлении модели рекомендуется заключить изменения в транзакцию `ILinkedUndoTransaction`. Это позволяет сгруппировать изменения в рамках одной транзакции. В случае сбоя любых изменений будет выполнен откат всей сборки. Если пользователь отменяет изменение, все изменения будут отменены.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Вложение  
 ![И в элементе ILayerModel ILayer могут содержаться в. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Слои (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) и модель слоев (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) могут содержать комментарии и слои.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>  
  
 Слой (`ILayer`) может содержаться в модели слоев (`ILayerModel`) или быть вложенным в другой `ILayer`.  
  
 Для создания комментария или слоя используйте методы создания в соответствующем контейнере.  
  
## <a name="dependency-links"></a>Связи зависимостей  
 Связь зависимости представлена объектом. Навигация для нее возможна в любом направлении:  
  
 ![ILayerDependencyLink соединяет два элемента Ilayer. ] (~/modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Чтобы создать связь зависимости, вызовите метод `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Комментарии  
 Комментарии могут содержаться внутри слоев или модели слоев, кроме того, они могут быть связаны с другим элементом слоя:  
  
 ![Комментарии можно прикрепить к любому элементу слоя. ] (~/modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Комментарий может быть связан с любым числом элементов (включая нуль).  
  
 Чтобы получить комментарии, прикрепленные к элементу слоя, используйте код:  
  
```c#  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  Свойство `Comments` слоя `ILayer` получает комментарии, вложенные в `ILayer`. Оно не получает комментарии, связанные с ним.  
  
 Создайте комментарий, вызвав метод `CreateComment()` в соответствующем контейнере.  
  
 Создайте связь, используя `CreateLink()` в комментарии.  
  
## <a name="layer-elements"></a>Элементы слоя  
 Все типы элементов, которые могут содержаться в модели, являются элементами слоя:  
  
 ![содержимое схемы зависимостей, содержит элементы Ilayerelement. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Свойства  
 Каждый `ILayerElement` включает словарь строк с именем `Properties`. Этот словарь можно использовать для присоединения произвольных сведений к любому элементу слоя.  
  
## <a name="artifact-references"></a>Ссылки на артефакты  
 Ссылка на артефакт (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) представляет собой ссылку между слоем и элементом проекта, такие как файл, класс или папка.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> Пользователи создают артефакты для создания слоя или добавить с помощью перетаскивания элементов из обозревателя решений, представление классов или обозреватель объектов на диаграмму зависимостей. К слою может быть привязано любое число ссылок на артефакты.  
  
 В каждой строке обозревателя слоев отображается ссылка на артефакт. Дополнительные сведения см. в разделе [создавать диаграммы зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Основные типы и методы, затрагиваемые ссылками на артефакты, следующие:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> Свойство Categories указывает, на какой тип артефакта имеется ссылка (например, класс, исполняемый файл или сборка). Категории определяют, каким образом идентификатор идентифицирует целевой артефакт.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A>Создает ссылку артефакта из <xref:EnvDTE.Project>или <xref:EnvDTE.ProjectItem>.</xref:EnvDTE.ProjectItem> </xref:EnvDTE.Project></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Это асинхронная операция. Поэтому обычно требуется предоставить метод обратного вызова, вызываемый при завершении создания.  
  
 Ссылки на артефакты слоя не следует путать с артефактами в схемах вариантов использования.  
  
## <a name="shapes-and-diagrams"></a>Фигуры и схемы  
 Для представления каждого элемента в модели слоев используются два объекта: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>и <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> 
          `IShape` представляет положение и размер фигуры на схеме. В моделях слоев каждый `ILayerElement` есть `IShape`и каждый `IShape` на зависимость схема имеет один `ILayerElement`. `IShape` также используется для моделей UML. Поэтому не каждому объекту `IShape` назначается элемент слоя.  
  
 Аналогичным образом, <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>отображается на одной <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>  
  
 В коде пользовательского обработчика команды или жеста можно получить текущую схему и текущий набор фигур, используя импорт `DiagramContext`:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Каждый элемент ILayerElement представлен фигурой IShape. ] (~/modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>и <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>также используются для отображения моделей UML.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> Дополнительные сведения см. в разделе [отображение модели UML на схемах](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление команд и жестов в схемы зависимостей](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Добавление пользовательской проверки архитектуры в схемы зависимостей](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Добавление пользовательских свойств в схемы зависимостей](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Схемы зависимостей: Справочник](../modeling/layer-diagrams-reference.md)   
 [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)   

