---
title: Предоставление пользовательского окна свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117529"
---
# <a name="providing-a-custom-properties-window"></a>Предоставление пользовательского окна свойств
Можно предоставить свой собственный **свойства** окна для данного проекта системы, вместо расширения **свойства** окна, предоставляемые [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки (IDE). Чаще всего обнаружены случай — когда вы самостоятельно реализовать объекта, находящегося в рамке окна.  
  
 В событии не реализуют объекта, находящегося в рамке окна, но по-прежнему иметь доступ к нему другими средствами, существует несколько способов доступа к <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейс, как указано в предыдущей процедуре на этой странице.  
  
### <a name="to-provide-your-properties-window"></a>Для предоставления окна свойств  
  
1. Определите идентификатор GUID, представляющий ваш **свойства** реализация окна.  
  
2. В вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> службы предложить вашей **свойства** окно от имени службы в среду Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Для вызова окна свойств  
  
1. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>.  
  
2. `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> из <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> переданные <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> метод.  
  
3. Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службы.  
  
4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> с первым параметром, значение `SEID_PropertyBrowserSID` (из <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> перечисления) и третий параметр, `varValue`, представляющее строковый формат идентификатора GUID, который представляет ваш **свойства** окно. Вызывать этот метод только один раз при первом создании вашей **свойства** окна документа. После вызова метода это **свойства** окно связан с вашей фрейм окна.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Чтобы получить объект фрейм окна, если вы не разработчик  
  
- Вы можете `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службы из <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> с параметром `propid` присвоено <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
- Активном окне документа можно получить, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> через службу SVsMonitorSelection. Задайте для параметра `elementid` для `SEID_WindowFrame`, взятый из <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> перечисления.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [Поля окна свойств и интерфейсы](../extensibility/internals/properties-window-fields-and-interfaces.md)