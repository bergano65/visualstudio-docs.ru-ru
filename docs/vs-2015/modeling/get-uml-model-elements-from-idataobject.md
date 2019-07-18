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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5f60338a8a856b4c6ef8fa913d6d7168ff67bb9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427040"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Получение элементов модели UML из IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Когда пользователь перетаскивает элементы из какого-либо источника на схему, перетащенные элементы кодируются в `System.Windows.Forms.IDataObject`. Кодировка зависит от типа исходного объекта. В приведенном ниже фрагменте кода показано, как извлекать элементы, если источником является UML-схема.  
  
> [!NOTE]
> Большинство операций, которые необходимо выполнять с моделями UML можно выполнить с помощью типов в определенных в сборках **Microsoft.VisualStudio.Uml.Interfaces** и  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Однако для этого нужно использовать некоторые классы, которые являются частью реализации средств моделирования UML. Например, класс `ShapeElement` в этом фрагменте не идентичен классу на UML-схеме `IShape`. Чтобы снизить риск приведения модели UML и схем в несовместимое состояние, не рекомендуется использовать вышеупомянутые методы при работе с данными классами реализации, за исключением случаев, когда нет других вариантов.  
  
## <a name="code-sample"></a>Образец кода  
 Проект должен содержать ссылки на следующие [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] сборки:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [версия]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [версия]**  
  
 **System.Windows.Forms**  
  
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
  
 Дополнительные сведения о `ElementGroupPrototype` и `Store` в которой реализуются средства моделирования UML, см. в разделе [пакет SDK моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="see-also"></a>См. также  
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)   
 [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
