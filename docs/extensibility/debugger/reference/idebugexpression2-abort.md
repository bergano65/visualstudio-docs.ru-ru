---
title: "IDebugExpression2::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::Abort"
helpviewer_keywords: 
  - "IDebugExpression2::Abort"
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод отменяет асинхронное вычисление выражений, как запускается вызовом [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) метод.  
  
## Синтаксис  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```c#  
int Abort();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда асинхронная вычисление выражений отменяется, не делает, отправленное [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) событие методу обратного вызова события к переданному  [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) OR  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) методы.  
  
## См. также  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)