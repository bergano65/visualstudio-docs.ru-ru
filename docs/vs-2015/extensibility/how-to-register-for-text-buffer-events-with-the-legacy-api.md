---
title: Практическое руководство. Регистрация для событий текстового буфера с помощью API прежних версий | Документация Майкрософт
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204094"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Практическое руководство. Регистрация событий текстового буфера с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы обращаетесь текстового буфера, используя старый API, должно зарегистрироваться для событий текстового буфера, как показано в следующей процедуре.  
  
### <a name="to-advise-text-buffer-events"></a>Чтобы уведомить текстовый буфер события  
  
1. Из указателя на один из интерфейсов на <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, вызовите `QueryInterface` для указателя на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2. Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> и передайте в идентификатор интерфейса событий, для которых вы хотите зарегистрировать.  
  
     Например, если вы хотите зарегистрировать для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, передается в интерфейсе идентификатор из IID_IVsTextLinesEvents.  
  
     Текстовый буфер возвращает указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для объекта точки подключения.  
  
3. С помощью этого указателя, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> метод, передав указатель на свою реализацию интерфейса событий, для которого вы хотите зарегистрировать, например, `IVsTextLinesEvents` интерфейс.  
  
     Среда возвращает файл cookie, который затем можно использовать чтобы остановить прослушивание событий путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> метод.  
  
## <a name="see-also"></a>См. также  
 [События текстового буфера в интерфейсе API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)
