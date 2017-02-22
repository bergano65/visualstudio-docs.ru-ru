---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
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
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод вычисляет выражение в асинхронном режиме.  
  
## Синтаксис  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### Параметры  
 `dwFlags`  
 \[in\] сочетание пометит из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, которое контролирует оценки выражений.  
  
 `pExprCallback`  
 \[in\] данный параметр всегда значение NULL.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Типичный код ошибки:  
  
|Ошибка|Описание|  
|------------|--------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Другое выражение было определено в данный момент, и параллельная вычисление выражений не поддерживается.|  
  
## Заметки  
 Этот метод должен возвращать сразу после запуска вычисление выражений.  Если выражение успешно вычислено, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) быть отправлено  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) обратный вызов события, как указано до конца  [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) OR  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Пример  
 В следующем примере показано, как реализовать этот метод для простого `CExpression` объект, реализующий  [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## См. также  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)