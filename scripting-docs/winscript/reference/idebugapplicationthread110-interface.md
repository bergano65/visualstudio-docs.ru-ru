---
title: Интерфейс IDebugApplicationThread110 | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44df7168c241c9a750354e1a603d6c5ba96dabd2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440538"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 — интерфейс
Предоставляет дополнительные функциональные возможности для [интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md) интерфейс.  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IDebugApplicationThread110` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Делает асинхронный вызов в основном потоке.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Счетчик количества запросов потока из потока PDM переключение механизмы в данный момент обрабатываются. Обычно 0 или 1, но, возможно, это будет больше, если один вызов поток начинает обработку, но вызывает синхронный вызов из потока или в противном случае приостанавливает работу потока (например, путем активации события IDebugApplicationEvents, которое выдается в отладчике поток)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) был вызван для этого потока и еще не завершена.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Этот поток находится в состоянии, которое может обрабатывать вызовы, выполненные с использованием потока PDM переключение механизмов (таких как SynchronousCallInThread).|