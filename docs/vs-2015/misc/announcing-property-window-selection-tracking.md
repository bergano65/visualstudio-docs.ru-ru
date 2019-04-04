---
title: Объявление о выпуске свойство окна выбора отслеживания | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1ef6984a21099bfad013ef97534d9984fa81d10d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989122"
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