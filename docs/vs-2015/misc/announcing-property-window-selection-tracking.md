---
title: Объявление о выпуске свойство окна выбора отслеживания | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bb2f2ceb7ed7faa3165f2346a0e0d14de1371166
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563312"
---
# <a name="announcing-property-window-selection-tracking"></a>Отслеживание выделения в окне свойств
Если вы хотите работать с **свойства** окна или **свойство** страниц, например, формы, текст или выделения, для которого требуется просмотреть свойства, то необходимо иметь полное представление о том, как вы Координируйте выбора. Например необходимо знать, есть ли у вас выбрать один элемент или множественный выбор. Затем необходимо объявлять тип выделения (одному или нескольким) в интегрированной среде разработки с помощью <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс. Этот интерфейс предоставляет сведения, необходимые **свойства** окна.  
  
### <a name="to-announce-selection-to-the-environment"></a>Рады сообщить о выбора в среде  
  
1.  Вызовите `QueryInterface` для <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  Чтобы сделать это, используйте указатель сайта передал в представление при его создании.  
  
    2.  Вызовите `QueryService` из представления для `SID_STrackSelection` службы.  
  
         Возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> метод каждый раз при изменении выбранные параметры и передать указатель на объект, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
     Объект-контейнер выделения можно использовать один или несколько выбранных элементов и содержит сведения о выборе в `IDispatch` объекта. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> метод уведомляет **свойства** окна, который был выделен. **Свойства** окно будет использовать объекты при <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для определения ли место один или несколько выбранных элементов, и каковы выбранных элементов для фактического объекта.  
  
     Если указать несколько, то **свойства** окно находит пересечение между общие свойства для объектов. Если указать один объект выделения, то **свойства** окно отображает все свойства для одного объекта.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [Страницы свойств](../extensibility/internals/property-pages.md)