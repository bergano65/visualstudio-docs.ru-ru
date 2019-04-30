---
title: Пример реализации вычисления выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95d89340d41b79339b5501092919dccad2005570
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420828"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Пример реализации вычисления выражений
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [вычислитель выражений управляемого образец](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Для **Watch** выражения окна, Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта. `IDebugExpressionContext2::ParseText` Создает экземпляр вычислитель выражений (EE) и вызывает метод [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.

 `IDebugExpressionEvaluator::Parse` Выполняет следующие задачи:

1. [C++ только] Выполняет синтаксический анализ выражения для поиска ошибок.

2. Создает экземпляр класса (называется `CParsedExpression` в этом примере), которое будет выполняться `IDebugParsedExpression` интерфейса и сохраняет в классе выражение для синтаксического анализа.

3. Возвращает `IDebugParsedExpression` интерфейс из `CParsedExpression` объекта.

> [!NOTE]
> В приведенных ниже примерах и в образце MyCEE средство оценки выражений не различал синтаксический анализ на основе оценки.

## <a name="managed-code"></a>Управляемый код
 Следующий код показывает реализацию `IDebugExpressionEvaluator::Parse` в управляемом коде. Эта версия метода откладывает для синтаксического анализа [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) код для синтаксического анализа, оценке и в то же время (см. в разделе [оценки выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
Следующий код представляет собой реализацию `IDebugExpressionEvaluator::Parse` в неуправляемом коде. Этот метод вызывает вспомогательную функцию, `Parse`, выполнить синтаксический анализ выражения и проверьте наличие ошибок, но этот метод игнорирует полученное значение. Оценка формальное отложено до [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) где синтаксический анализ выражения во время его оценки (см. в разделе [оценки выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Оценка выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Оценка выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)