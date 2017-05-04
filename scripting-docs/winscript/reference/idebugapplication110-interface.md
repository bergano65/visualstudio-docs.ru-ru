---
title: "IDebugApplication110 — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 — интерфейс"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 — интерфейс
Интерфейс `IDebugApplication110` расширяющий функциональность [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  Можно получить экземпляр этого интерфейса путем вызова QueryInterface для реализации [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Этот интерфейс реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Интерфейс `IDebugApplication110` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Вызывает синхронный в основном потоке.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Вызывает асинхронный вызов в основном потоке.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Ожидания для всех указанных маркеров, которые необходимо указать при крест\- включая вызовы потока, который необходимо создать в этот поток.  Этот метод должен вызываться из потока отладчика.|