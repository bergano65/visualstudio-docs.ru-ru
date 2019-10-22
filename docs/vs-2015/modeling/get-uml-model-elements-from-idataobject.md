---
title: Получение элементов модели UML из IDataObject | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666079"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Получение элементов модели UML из IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Когда пользователь перетаскивает элементы из какого-либо источника на схему, перетащенные элементы кодируются в `System.Windows.Forms.IDataObject`. Кодировка зависит от типа исходного объекта. В приведенном ниже фрагменте кода показано, как извлекать элементы, если источником является UML-схема.

> [!NOTE]
> Большинство операций, которые необходимо выполнить в моделях UML, можно выполнить с помощью типов, определенных в сборках **Microsoft. VisualStudio. UML. interfaces** и **Microsoft. VisualStudio. арчитектуретулс. Extensibility**. Однако для этого нужно использовать некоторые классы, которые являются частью реализации средств моделирования UML. Например, класс `ShapeElement` в этом фрагменте не идентичен классу на UML-схеме `IShape`. Чтобы снизить риск приведения модели UML и схем в несовместимое состояние, не рекомендуется использовать вышеупомянутые методы при работе с данными классами реализации, за исключением случаев, когда нет других вариантов.

## <a name="code-sample"></a>Образец кода
 Проект должен ссылаться на следующие сборки [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]:

 **Microsoft. VisualStudio. моделирования. SDK. систему**

 **Microsoft. VisualStudio. моделирование. SDK. схемы. систему**

 **System. Windows. Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 Дополнительные сведения о `ElementGroupPrototype` и `Store`, в которых реализуются средства моделирования UML, см. в разделе [пакет SDK для моделирования для Visual Studio — языки, относящиеся к домену](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>См. также раздел
 [Программирование с помощью API UML](../modeling/programming-with-the-uml-api.md) [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
