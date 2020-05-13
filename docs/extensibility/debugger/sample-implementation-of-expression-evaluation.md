---
title: Примерная реализация оценки экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713100"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Пример реализации оценки выражений
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Для выражения окна **Watch** Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания объекта [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`мгновенно оценивает выражение (EE) и вызывает [Parse,](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) чтобы получить объект [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 Выполняет `IDebugExpressionEvaluator::Parse` следующие задачи:

1. (только си) Сравнивает выражение для поиска ошибок.

2. Мгновения класса `CParsedExpression` (называется в этом `IDebugParsedExpression` примере), который запускает интерфейс и хранит в классе выражение, которое будет разогнано.

3. Возвращает `IDebugParsedExpression` интерфейс с `CParsedExpression` объекта.

> [!NOTE]
> В примерах, которые следуют за выборкой MyCEE, оценщик выражения не отделяет разбор от оценки.

## <a name="managed-code"></a>Управляемый код
 Следующий код показывает `IDebugExpressionEvaluator::Parse` реализацию управляемого кода. Эта версия метода откладывает разбор [для EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) как код для разбора также оценивает в то же время [(см. Оценить выражение Watch).](../../extensibility/debugger/evaluating-a-watch-expression.md)

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Неуправляемый код
Следующий код — `IDebugExpressionEvaluator::Parse` это реализация неуправляемого кода. Этот метод вызывает функцию `Parse`помощника, чтобы разобрать выражение и проверить на наличие ошибок, но этот метод игнорирует полученное значение. Официальная оценка откладывается до [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) где выражение разбирается во время оценки (см. [Оценить выражение Watch).](../../extensibility/debugger/evaluating-a-watch-expression.md)

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>См. также
- [Оценка выражения окна Watch](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Оценка выражения Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)
