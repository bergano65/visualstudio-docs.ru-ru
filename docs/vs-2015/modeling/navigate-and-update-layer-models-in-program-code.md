---
title: Навигация и обновление моделей слоев в программном коде | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668575"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Перемещение по моделям слоев в коде программы и их обновление
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе рассматриваются элементы и отношения в моделях слоев, к которым можно перейти и которые можно обновить с помощью программного кода. Дополнительные сведения о схемах слоев с точки зрения пользователя см. в разделе [схемы слоев: Справочник](../modeling/layer-diagrams-reference.md) и [схемы слоев. рекомендации](../modeling/layer-diagrams-guidelines.md).

 Модель `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer`, описываемая в этом разделе, является интерфейсом более общей модели <xref:Microsoft.VisualStudio.GraphModel>. При написании [команды меню или расширения жеста](../modeling/add-commands-and-gestures-to-layer-diagrams.md)используйте `Layer` модель. При написании [расширения проверки слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)проще использовать `GraphModel` .

## <a name="transactions"></a>Транзакции
 При обновлении модели рекомендуется заключить изменения в транзакцию `ILinkedUndoTransaction`. Это позволяет сгруппировать изменения в рамках одной транзакции. В случае сбоя любых изменений будет выполнен откат всей сборки. Если пользователь отменяет изменение, все изменения будут отменены.

 Дополнительные сведения см. в разделе [Связывание обновлений модели UML с помощью транзакций](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Containment
 ![Элементы ILayer могут содержаться в как в элементе ILayer, так и в элементе ILayerModel.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Слои ([илайер](/previous-versions/ff644251(v=vs.140))) и модель слоев ([илайермодел](/previous-versions/ff643069(v=vs.140))) могут содержать комментарии и слои.

 Слой (`ILayer`) может содержаться в модели слоев (`ILayerModel`) или быть вложенным в другой `ILayer`.

 Для создания комментария или слоя используйте методы создания в соответствующем контейнере.

## <a name="dependency-links"></a>Связи зависимостей
 Связь зависимости представлена объектом. Навигация для нее возможна в любом направлении:

 ![ILayerDependencyLink соединяет два элемента ILayer.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Чтобы создать связь зависимости, вызовите метод `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Комментарии
 Комментарии могут содержаться внутри слоев или модели слоев, кроме того, они могут быть связаны с другим элементом слоя:

 ![Комментарии можно прикрепить к любому элементу слоя.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Комментарий может быть связан с любым числом элементов (включая нуль).

 Чтобы получить комментарии, прикрепленные к элементу слоя, используйте код:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> Свойство `Comments` слоя `ILayer` получает комментарии, вложенные в `ILayer`. Оно не получает комментарии, связанные с ним.

 Создайте комментарий, вызвав метод `CreateComment()` в соответствующем контейнере.

 Создайте связь, используя `CreateLink()` в комментарии.

## <a name="layer-elements"></a>Элементы слоя
 Все типы элементов, которые могут содержаться в модели, являются элементами слоя:

 ![Схема слоев содержит элементы ILayerElement.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Свойства
 Каждый `ILayerElement` включает словарь строк с именем `Properties`. Этот словарь можно использовать для присоединения произвольных сведений к любому элементу слоя.

## <a name="artifact-references"></a>Ссылки на артефакты
 Ссылка артефакта ([илайерартифактреференце](/previous-versions/ff644536(v=vs.140))) представляет собой ссылку между слоем и элементом проекта, например файлом, классом или папкой. Пользователи создают артефакты, создавая слои или перетаскивая в них элементы из обозревателя решений, представления класса или обозревателя объектов. К слою может быть привязано любое число ссылок на артефакты.

 В каждой строке обозревателя слоев отображается ссылка на артефакт. Дополнительные сведения см. в статье [Создание схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md).

 Основные типы и методы, затрагиваемые ссылками на артефакты, следующие:

 [Илайерартифактреференце](/previous-versions/ff644536(v=vs.140)). Свойство Categories указывает, на какой тип артефакта имеется ссылка (например, класс, исполняемый файл или сборка). Категории определяют, каким образом идентификатор идентифицирует целевой артефакт.

 [Артифактреференцеекстенсионс. креатеартифактреференцеасинк](/previous-versions/ff695840(v=vs.140)) создает ссылку артефакта из <xref:EnvDTE.Project> или <xref:EnvDTE.ProjectItem> . Это асинхронная операция. Поэтому обычно требуется предоставить метод обратного вызова, вызываемый при завершении создания.

 Ссылки на артефакты слоя не следует путать с артефактами в схемах вариантов использования.

## <a name="shapes-and-diagrams"></a>Фигуры и схемы
 Для представления каждого элемента в модели слоев используются два объекта: `ILayerElement` и [ишапе](/previous-versions/ee806673(v=vs.140)). `IShape` представляет положение и размер фигуры на схеме. В модели слоев каждому `ILayerElement` назначается один объект `IShape`, а каждому объекту `IShape` на схеме слоя — один элемент `ILayerElement`. `IShape` также используется для моделей UML. Поэтому не каждому объекту `IShape` назначается элемент слоя.

 Аналогичным образом, `ILayerModel` отображается в одном [идиаграм](/previous-versions/ee789658(v=vs.140)).

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

 ![Каждый элемент ILayerElement представлен фигурой IShape.](../modeling/media/layerapi-shapes.png)

 [Ишапе](/previous-versions/ee806673(v=vs.140)) и [идиаграм](/previous-versions/ee789658(v=vs.140)) также используются для вывода моделей UML. Дополнительные сведения см. в разделе [Отображение UML-модели на схемах](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>См. также раздел

- [Добавление команд и жестов в схемы слоев](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Добавление пользовательских свойств в схемы слоев](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)
- [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)
- [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)
