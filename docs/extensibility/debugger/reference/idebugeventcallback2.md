---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс используется обработчиком отладки \(DE\) отправлять отладочные события в сеансе отладки \(SDM manager\).  
  
## Синтаксис  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## Примечания по реализации  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] реализует этот интерфейс для получения событий из обработчика отладки.  
  
## Замечания для вызывающих объектов  
 Отладчик получает этот интерфейс обычно при вызове SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)"  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)или  [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  Отладчик отправляет события в SDM, вызвав [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugEventCallback2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Отправляет уведомление событий отладки в SDM.|  
  
## Заметки  
 Как [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и  [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) укажите, что они принимают  `IDebugEventCallback2` интерфейс, это не так и указатель интерфейса всегда будет иметь значение NULL.  Вместо этого отладчик должен использовать `IDebugEventCallback2` интерфейс полученного при вызове метода  [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)"  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)или  [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Если пакет реализует [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) в управляемом коде, строго о этому  <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> вызовите на разных интерфейсах, передайте значение  [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)