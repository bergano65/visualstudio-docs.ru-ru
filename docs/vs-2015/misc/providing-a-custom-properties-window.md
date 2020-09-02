---
title: Предоставление настраиваемого окна свойств | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810710"
---
# <a name="providing-a-custom-properties-window"></a>Предоставление пользовательского окна свойств
Вместо расширения окна **свойств** , предоставленного **Properties** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной средой разработки (IDE), можно предоставить собственное окно свойств для конкретной системы проектов. Наиболее часто обнаруживаемый сценарий заключается в реализации объекта, наличного в рамке окна.  
  
 В случае, если объект не реализуется в фрейме окна, но по-прежнему имеет доступ к нему другими способами, существует ряд способов доступа к <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> интерфейсу, как указано в последней процедуре на этой странице.  
  
### <a name="to-provide-your-properties-window"></a>Предоставление окно свойств  
  
1. Определите идентификатор GUID, представляющий реализацию окна **свойств** .  
  
2. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации используйте <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> службу, чтобы предложить окно **свойств** как службу в среду Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Вызов окна свойств  
  
1. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> из из, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> переданного в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> метод.  
  
3. Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службы.  
  
4. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> с первым параметром, установленным в `SEID_PropertyBrowserSID` (берется из <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> перечисления), и третьим параметром, `varValue` ПРЕДСТАВЛЯЮЩИМ форму строки идентификатора GUID, который представляет окно **свойств** . Этот вызов следует выполнять только один раз при первом создании окна документа в окне " **Свойства** ". После вызова это окно **свойств** связано с рамкой окна.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Получение объекта фрейма окна, если вы не являетесь разработчиком  
  
- `QueryService`Для службы можно <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> задать параметр со `propid` значением <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Окно активного документа можно получить, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> через службу свсмониторселектион. Задайте для параметра `elementid` значение `SEID_WindowFrame` , взятое из <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> перечисления.  
  
## <a name="see-also"></a>См. также:  
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md)