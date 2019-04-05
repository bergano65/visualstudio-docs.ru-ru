---
title: Объект VSTextView | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8ed14761b77e3469b2c19d0e9fd2ff3732bb72d
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2019
ms.locfileid: "59002110"
---
# <a name="vstextview-object"></a>Объект VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представление текста — это окно, который позволяет пользователю просматривать и редактировать текст в Юникоде текстового буфера. По сути это представление является то, что большинство пользователей называть редактора. Так как представление отделяется различные уровни текста (перенос по словам, структуры текста и т. д.) из буфера, представление не гарантированно точное представление текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 В следующей таблице показаны интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Разрешает создание составных действий (то есть действия, которые группируются в единое единый отмены и повтора).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы для управления и доступ к представлению. `IVsTextView` не является потокобезопасным.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет область окна.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с уровнями текста.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|  
  
## <a name="see-also"></a>См. также  
 [Изменение фигур](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
