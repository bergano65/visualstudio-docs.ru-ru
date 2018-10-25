---
title: IDebugExpression2::EvaluateAsync | Документация Майкрософт
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
ms.openlocfilehash: e7906e1f1daa0b473473abd28417a2db1c9b7f98
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912829"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Этот метод вычисляет выражение асинхронно.  
  
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
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, управлять вычисления выражения.  
  
 `pExprCallback`  
 [in] Этот параметр всегда является значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. — Типичный код ошибки:  
  
|Error|Описание|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Сейчас вычисляется другого выражения и вычисление одновременных выражений не поддерживается.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен возвращать сразу после ее запуска оценки выражения. Если выражение успешно вычисляется, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) должны быть отправлены [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) обратный вызов события, передаваемой через [Attach ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [присоединить](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CExpression` объект, реализующий [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс.  
  
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