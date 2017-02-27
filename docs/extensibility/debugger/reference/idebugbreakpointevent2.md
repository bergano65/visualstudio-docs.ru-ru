---
title: "IDebugBreakpointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugBreakpointEvent2"
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) отправляет этот интерфейс для сеанса отладки \(SDM\) диспетчер когда программа останавливается в точке останова.  
  
## Синтаксис  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс в процессе поддержки для точек останова.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован в одном объекте, как этот интерфейс \(SDM использует  [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс\).  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события, если хотя бы одна обнаружении точки останова в программе.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставляемая SDM, когда он вложен в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugBreakpointEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Создает перечислитель для всех точек останова, сгорели в текущем расположении кода.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)