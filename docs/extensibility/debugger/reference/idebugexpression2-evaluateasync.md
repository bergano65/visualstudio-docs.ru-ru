---
title: "IDebugExpression2::EvaluateAsync | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aaaf66616722739ad51b07e75470f6edfde5c1b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Error|Описание:|  
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