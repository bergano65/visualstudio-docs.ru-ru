---
title: Объект VSTextView | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a09a4911eca71565b39ffdfab3cc31ec92233e06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561709"
---
# <a name="vstextview-object"></a>Объект VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [объект VSTextView](https://docs.microsoft.com/visualstudio/extensibility/vstextview-object).  
  
Представление текста — это окно, который позволяет пользователю просматривать и редактировать текст в Юникоде текстового буфера. По сути это представление является то, что большинство пользователей называть редактора. Так как представление отделяется различные уровни текста (перенос по словам, структуры текста и т. д.) из буфера, представление не гарантированно точное представление текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 В следующей таблице показаны интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Разрешает создание составных действий (то есть действия, которые группируются в единое единый отмены и повтора).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы для управления и доступ к представлению. `IVsTextView` не является потокобезопасным.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет область окна.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с уровнями текста.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|  
  
## <a name="see-also"></a>См. также  
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

