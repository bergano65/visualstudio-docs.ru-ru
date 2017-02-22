---
title: "IDebugBreakpointBoundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointBoundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2"
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointBoundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс определяет сеанс отладки \(SDM\), диспетчер ожидающих точке останова успешно привязала загруженной в программе.  
  
## Синтаксис  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс в процессе поддержки для точек останова.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда ожидается точка останова привязана к успешно отлаживаемой программы.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugBreakpointBoundEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Получает завершения отложенной точку останова, привязки.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Создает перечислитель точки останова, которые были привязанны об этом событии.|  
  
## Заметки  
 Если точка останова привязана, событие отправляется SDM.  Если точка останова, то нельзя привязать [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) отправляет; в противном случае \-  `IDebugBreakpointBoundEvent2` отправить.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)