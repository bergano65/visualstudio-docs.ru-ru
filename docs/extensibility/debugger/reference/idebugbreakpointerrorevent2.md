---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс определяет сеанс отладки \(SDM\), диспетчер ожидается точка останова не может быть привязана, загруженной в программе или по причине предупреждения или ошибки.  
  
## Синтаксис  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс в процессе поддержки для точек останова.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда ожидается точка останова невозможно привязать к отлаживаемой программы.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugBreakpointErrorEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Возвращает IDebugErrorBreakpoint2 интерфейс, который описывает предупреждения или ошибки.|  
  
## Заметки  
 Если точка останова привязана, событие отправляется SDM.  Если точка останова, то нельзя привязать `IDebugBreakpointErrorEvent2` отправляет; в противном случае \-  [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) отправить.  
  
 Например, если условие, связанное с точкой останова, ожидающих не удается выполнить синтаксический анализ или оценивать, предупреждение, которое отправляется ожидается точка останова невозможно привязать в настоящее время.  Это может происходить, если код для точки останова не загрузил.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)