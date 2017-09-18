---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Разрешает или запрещает\) вычисление выражений в данном потоке, даже если программа остановлена.  
  
## Синтаксис  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### Параметры  
 `pOriginatingProgram`  
 \[in\] IDebugProgram2 объект, представляющий программу, которая оценивает выражение.  
  
 `dwTid`  
 \[in\] определяет идентификатор потока.  
  
 `dwEvalFlags`  
 \[in\] сочетание пометит из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, указывающее как вычисление, которое нужно выполнить.  
  
 `pExprCallback`  
 \[in\] IDebugEventCallback2 объект, который будет использоваться отправлять отладочные события, происходящие во время оценки выражений.  
  
 `fWatch`  
 \[in\] если не равен нулю \(`TRUE`\), позволяющий вычисление выражений в потоке, указанном контекстом by  `dwTid`; в противном случае \- нуль \(`FALSE`\) запрещает вычисление выражений в этом потоке.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда сеанс отладки \(SDM\) запрашивает диспетчера программы, указанную `pOriginatingProgram` параметр вычислить значение выражения, она извещает все другие вложенные программы, вызвав этот метод.  
  
 Вычисление выражений в одной программе может привести к тому, что выполнение кода в другом, должно вычислении функции или оценке любых `IDispatch` свойства.  Вследствие этого, этот метод разрешает вычисление выражений для запуска и окончания, даже если поток может быть остановлен в этой программе.  
  
## См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)