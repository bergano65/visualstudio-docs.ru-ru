---
title: Как зарегистрировать события текстового буфера с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204094"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Практическое руководство. Регистрация событий текстового буфера с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При доступе к текстовому буферу с помощью API прежних версий следует зарегистрировать события текстового буфера, как показано в следующей процедуре.  
  
### <a name="to-advise-text-buffer-events"></a>Для уведомления о событиях текстового буфера  
  
1. Из указателя на один из интерфейсов в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> вызывается метод `QueryInterface` для указателя на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> метод и передайте идентификатор интерфейса событий, для которых необходимо выполнить регистрацию.  
  
     Например, если вы хотите зарегистрироваться для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , передайте идентификатор интерфейса IID_IVsTextLinesEvents.  
  
     Текстовый буфер возвращает указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для соответствующего объекта точки соединения.  
  
3. Используя этот указатель, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> метод, передав в него указатель на реализацию интерфейса событий, для которого требуется зарегистрировать, например `IVsTextLinesEvents` интерфейс.  
  
     Среда возвращает файл cookie, который затем можно использовать для прекращения прослушивания событий путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> метода.  
  
## <a name="see-also"></a>См. также:  
 [События текстового буфера в интерфейсе API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)
