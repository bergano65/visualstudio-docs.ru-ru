---
title: Объект Встекствиев | Документация Майкрософт
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
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690688"
---
# <a name="vstextview-object"></a>Объект VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовое представление — это окно, позволяющее пользователям просматривать и изменять текст в Юникоде для текстового буфера. По сути, представление — это то, что большинство пользователей ссылается на редактор. Так как представление отделяется от буфера различными текстовыми слоями (перенос по словам, структурирование текста и т. д.), представление не обязательно должно быть точным представлением текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к представлению сетекст с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) .  
  
 В следующей таблице показаны интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекте.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|[идропсаурце](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (то есть действия, сгруппированные в одну единицу отмены или возврата).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет базовые методы для управления представлением и доступа к ним. `IVsTextView`Интерфейс  не является потокобезопасным.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет областью окна.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с текстовыми слоями.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции с представлением из другого потока.|  
  
## <a name="see-also"></a>См. также:  
 [Изменение фигур](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Объект Встекстбуффер](../extensibility/vstextbuffer-object.md)   
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
