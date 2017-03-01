---
title: "Объект VSTextView | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
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
ms.openlocfilehash: fd11409382b2db5e5cbea8c0dad25dbdb3b6cb99
ms.lasthandoff: 02/22/2017

---
# <a name="vstextview-object"></a>Объект VSTextView
Текстовое представление — окно, которое позволяет пользователям просматривать и редактировать текст в формате Юникод текстового буфера. По существу это представление является то, что большинство пользователей называть редактора. Так как представление разделены из буфера различные слои текста (перенос по словам, структуры текста и т.д.), представление не гарантированно точное представление текста в буфере. Дополнительные сведения о представлении текста в разделе [доступ к theText представление с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 В следующей таблице показаны интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>объекта.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget></xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite></xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (действия, сгруппированные в единое одной отмены или повтора).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы для управления и доступа к представлению. `IVsTextView`не является потокобезопасным.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет область окна.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с слои текста.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|  
  
## <a name="see-also"></a>См. также  
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Доступ к theText представление с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
