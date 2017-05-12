---
title: "IDebugApplicationThread110 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 — интерфейс"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 — интерфейс
Предоставляет больше возможностей для интерфейса [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md).  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IDebugApplicationThread110` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Вызывает асинхронный вызов в основном потоке.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Число, сколько потоков в пул из механизмов передачи потока PDM в настоящий момент.  Обычно 0 или 1, но возможны для этого будет выше при запуске одного вызова поток, обрабатывающий но активируют синхронный вызов из потока или в противном случае приостановят поток \(например, путем активировать событие IDebugApplicationEvents, которое выдается в потоке отладчика\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) было Позвонитьо в этом потоке и еще не завершено.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Этот поток в состоянии, не может обработать, вызываемые с помощью механизмов передачи потока PDM \(например, SynchronousCallInThread\).|