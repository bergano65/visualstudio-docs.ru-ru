---
title: IDebugExpression2:ОценкаАсинк (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729750"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Этот метод оценивает выражение асинхронно.

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

## <a name="parameters"></a>Параметры
`dwFlags`\
(в) Комбинация флагов из перечисления [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) которые контролируют оценку выражения.

`pExprCallback`\
(в) Этот параметр всегда является нулевым значением.

## <a name="return-value"></a>Возвращаемое значение
В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки. Типичный код ошибки:

|Error|Описание|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|В настоящее время проводится оценка другого выражения, и одновременная оценка выражения не поддерживается.|

## <a name="remarks"></a>Примечания
Этот метод должен вернуться сразу же после начала оценки выражения. При успешной оценке выражения [IDebugExpressionEvaluationCompleteEventEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) должен быть отправлен на обратный вызов события [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) по мере отправки через [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) или [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="example"></a>Пример
В следующем примере показано, как `CExpression` реализовать этот метод для простого объекта, который реализует интерфейс [IDebugExpression2.](../../../extensibility/debugger/reference/idebugexpression2.md)

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
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
