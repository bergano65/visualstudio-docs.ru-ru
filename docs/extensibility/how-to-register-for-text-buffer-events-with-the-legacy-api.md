---
title: "Как: регистрация событий буфера текста с помощью прежних версий API | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 94f2e781c316f3891fdef0c324d54fa2f9742222
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Как: регистрация событий буфера текста с помощью API прежних версий
При доступе к буфер текста с помощью предыдущих версий API, следует зарегистрировать для текстового буфера событий, как показано в следующей процедуре.  
  
### <a name="to-advise-text-buffer-events"></a>Чтобы уведомить событий текстового буфера  
  
1.  Из указателя на один из интерфейсов на <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, вызовите `QueryInterface` для указателя на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> и передайте в идентификатор интерфейса событий, для которых вы хотите зарегистрировать.  
  
     Например, если вы хотите зарегистрировать для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, то передайте в интерфейс идентификатор IID_IVsTextLinesEvents.  
  
     Буфер текста возвращает указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для объекта точки подключения.  
  
3.  С помощью этого указателя, вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> метод, передавая указатель на вашу реализацию интерфейса событий, для которого вы хотите зарегистрировать, например, `IVsTextLinesEvents` интерфейс.  
  
     Среда возвращает файл cookie, который затем можно использовать для остановки прослушивание событий путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> метод.  
  
## <a name="see-also"></a>См. также  
 [Текст события буфера в API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)