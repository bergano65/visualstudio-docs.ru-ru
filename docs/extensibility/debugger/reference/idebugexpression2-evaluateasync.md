---
title: IDebugExpression2::EvaluateAsync | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13364d94f33eca33bf71b7077c19b9da54298ed7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Этот метод асинхронно вычисляет выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, обеспечивающие управление вычисления выражения.  
  
 `pExprCallback`  
 [in] Этот параметр всегда имеет значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Код ошибки обычно является:  
  
|Error|Описание|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Другое выражение вычисляется, и вычисление выражений одновременных не поддерживается.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен возвращать сразу же после его начала вычисления выражения. Когда вычисляется выражение [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) должен быть отправлен [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) события обратного вызова, как указываются через [присоединения ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [присоединения](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простой `CExpression` объект, реализующий [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейса.  
  
```cpp  
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
  
## <a name="see-also"></a>См. также  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)