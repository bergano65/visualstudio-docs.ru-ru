---
title: 'Практическое: регистрация для событий текстового буфера с помощью API прежних версий | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e895f2d67c23454ad3f7481e558f6dde542867b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782782"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Практическое: регистрация для событий текстового буфера с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы обращаетесь текстового буфера, используя старый API, должно зарегистрироваться для событий текстового буфера, как показано в следующей процедуре.  
  
### <a name="to-advise-text-buffer-events"></a>Чтобы уведомить текстовый буфер события  
  
1.  Из указателя на один из интерфейсов на <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, вызовите `QueryInterface` для указателя на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> и передайте в идентификатор интерфейса событий, для которых вы хотите зарегистрировать.  
  
     Например, если вы хотите зарегистрировать для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, передается в интерфейсе идентификатор из IID_IVsTextLinesEvents.  
  
     Текстовый буфер возвращает указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для объекта точки подключения.  
  
3.  С помощью этого указателя, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> метод, передав указатель на свою реализацию интерфейса событий, для которого вы хотите зарегистрировать, например, `IVsTextLinesEvents` интерфейс.  
  
     Среда возвращает файл cookie, который затем можно использовать чтобы остановить прослушивание событий путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> метод.  
  
## <a name="see-also"></a>См. также  
 [События текстового буфера в интерфейсе API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)

