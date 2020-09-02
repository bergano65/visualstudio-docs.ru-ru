---
title: Объявление об отслеживании выбора окна свойств | Документация Майкрософт
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
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002451"
---
# <a name="announcing-property-window-selection-tracking"></a>Отслеживание выделения в окне свойств
Если вы хотите работать с окном **свойств** или со страницами **свойств** , например с формой, текстом или выделением, для которого требуется просмотреть свойства, необходимо иметь полное знание о том, как координировать выборку. Например, необходимо определить, имеется ли один выбор или несколько вариантов выбора. Затем необходимо объявить тип выбора (один или несколько) с интегрированной средой разработки с помощью <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейса. Этот интерфейс предоставляет сведения, необходимые для окна " **Свойства** ".  
  
### <a name="to-announce-selection-to-the-environment"></a>Объявление выбора в среде  
  
1. Вызовите метод `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Для этого используйте указатель сайта, переданный в представление при его создании.  
  
    2. Вызовите `QueryService` из представления для `SID_STrackSelection` службы.  
  
         Он возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> метод при каждом изменении выбора и передайте указатель на объект, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     Объект контейнера выбора может использовать один или несколько элементов и содержит сведения о выборе в `IDispatch` объекте. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> метода уведомляет окно **свойств** о том, что выделение изменилось. Затем в окне **Свойства** используются объекты <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , чтобы определить, были ли выполнены один или несколько вариантов выбора и каковы фактические значения выбора объектов.  
  
     Если указать множественный выбор, то в окне « **Свойства** » будет обнаружено пересечение между общими свойствами объектов. Если указать один объект, в окне **Свойства** отобразятся все свойства для одного объекта.  
  
## <a name="see-also"></a>См. также:  
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [Страницы свойств](../extensibility/internals/property-pages.md)