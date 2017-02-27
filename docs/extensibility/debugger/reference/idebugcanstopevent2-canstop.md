---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) уведомляет ли остановка на текущем месте кода или не просто возобновить выполнение.  
  
## Синтаксис  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### Параметры  
 `fCanStop`  
 \[in\] ненулевое значение \(`TRUE`если DE\) должен прерывается на текущем месте кода; в противном случае \- нуль \(`FALSE`\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Получатель данного события обычно вызывает [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) метод, чтобы определить причину DE хочет остановить, а затем вызывает  `IDebugCanStopEvent2::CanStop` метод с соответствующим ответом.  
  
 Если DE останавливается, он отправляет событие, описывающее причину для остановки.  Обычно 2 событий, отправляются пользователю или ввода, представленные break [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) интерфейс и событие точки останова, представленное  [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс.  
  
## См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)