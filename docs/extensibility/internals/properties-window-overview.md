---
title: "Общие сведения об окне свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>Общие сведения об окне свойств
**Свойства** окно используется для отображения свойств для объектов, выбранных в два основных типа окон [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Эти два типа окон являются:  
  
-   Окна инструментов, такие как обозреватель решений, представление классов и объектов обозревателя  
  
-   Окон документов, содержащих такие редакторы и конструкторы, как конструктор форм, редактор XML и HTML-редактора  
  
## <a name="using-the-properties-window"></a>С помощью окна свойств  
 **Свойства** окне отображаются свойства одного или нескольких выбранных элементов. Если выбрано несколько элементов отображается пересечение всех свойств для всех выбранных объектов.  
  
 События, связанные с выбранного объекта в окне конструктора формы или HTML-редактора, используя метаданные COM +, отображаются в **свойства** окна. Например, можно выбрать кнопку и отобразить его связанных событий, таких как `OnClick` события, которые могут быть связаны с этой кнопки.  
  
 События, отображаемые в **свойства** окна в основном используются с объектами, которые привязаны к коду. При редактировании формат файла, который не имеет ничего общего с кодом, не будет иметь никаких событий. События отображаются только в **свойства** окна после привязки между запуском кода и некоторые события, связанные с конкретными объектами. Пример этого будет кода программной части выбранного объекта, который выполняется при активации этого объекта.  
  
 В следующей таблице перечислены используемые интерфейсы **свойства** окна.  
  
|Имя интерфейса|Описание|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Список категорий для **свойства** окна и каждое свойство сопоставляется категории.|  
|[Интерфейс IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Предоставляет методы и свойства для программных средств и других приложений, поддерживающих автоматизацию объекта.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Содержит кнопки с многоточием (...) называется *построители* , откройте windows модальное диалоговое окно, реализуемый сам объект. Используется, если значение не является типизированным легко пользователем в текстовое поле. Например он может использоваться для открытия палитру цветов, определяющее значение RGB для вас.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Предоставляет доступ к объектам, которые используются для обновления сведений, отображаемых в **свойства** окна. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>реализуется VSPackages для каждого окна, содержащего выбираемые объекты с связанных свойств для отображения.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Предоставляет сведения о типе объекта, например методы интерфейса и полей структуры.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Позволяет VSPackages для получения уведомлений о событиях выбора и для получения сведений о текущей иерархии проектов, элементов, значение элемента и контекст пользовательского интерфейса командной строки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Предоставляет среду с доступом к множественный выбор.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Используется для предоставления локализованные имена для некоторых свойств отображается в **свойства** окна.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Уведомляет зарегистрированные VSPackages изменения текущего выбора, значение элемента или контекст пользовательского интерфейса командной строки.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Уведомляет среду изменений в выделенном фрагменте и предоставляет доступ к иерархии и элемент информации, относящейся к новое выделение.|  
  
 Дополнительные сведения о `IDispatch`, см. в библиотеке MSDN.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)   
 [Поля окна свойств и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md)
