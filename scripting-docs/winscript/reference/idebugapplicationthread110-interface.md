---
title: "Idebugapplicationthread110 — интерфейс | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 — интерфейс
Предоставляет дополнительные функциональные возможности для [idebugapplicationthread — интерфейс](../../winscript/reference/idebugapplicationthread-interface.md) интерфейс.  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugApplicationThread110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Выполняет асинхронный вызов в основном потоке.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Количество обрабатываемых в настоящий момент количество потоков запросов из потока PDM переключение механизмы. Обычно 0 или 1, но, возможно, это может быть выше, если один поток вызов запускает обработку, но активирует синхронный вызов из потока или в противном случае приостанавливает работу потока (например, путем активации события IDebugApplicationEvents, которое выдается в отладчике поток)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) был вызван для этого потока и еще не завершено.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Этот поток находится в состоянии, которое может обрабатывать вызовы, выполненные с помощью потока PDM переключение механизмы (например, SynchronousCallInThread).|