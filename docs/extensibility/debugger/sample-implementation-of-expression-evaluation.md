---
title: Пример реализации вычисления выражения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edc31a8bc403f4f6dfcb16847d3cfce5d99b526
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-expression-evaluation"></a>Пример реализации вычисление выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Для **Контрольные значения** окно выражение, Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта. `IDebugExpressionContext2::ParseText` Создает экземпляр вычислитель выражений (EE) и вызывает метод [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
 Эта реализация `IDebugExpressionEvaluator::Parse` выполняет следующие задачи:  
  
1.  [C++] Выполняет синтаксический анализ выражения для поиска ошибок.  
  
2.  Создает экземпляр класса (называется `CParsedExpression` в этом примере), реализующий `IDebugParsedExpression` интерфейс и сохраняет в классе выражение для синтаксического анализа.  
  
3.  Возвращает `IDebugParsedExpression` интерфейс из `CParsedExpression` объекта.  
  
> [!NOTE]
>  В примерах ниже и в образце MyCEE средство оценки выражений не разделяйте синтаксический анализ на основе оценки.  
  
## <a name="managed-code"></a>Управляемый код  
 Это реализация `IDebugExpressionEvaluator::Parse` в управляемом коде. Обратите внимание, что эта версия метода откладывает для синтаксического анализа [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) как код для синтаксического анализа также проверяет, в то же время (в разделе [вычисления выражения для контроля](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Это реализация `IDebugExpressionEvaluator::Parse` в неуправляемом коде. Этот метод вызывает вспомогательную функцию `Parse`, выполнить синтаксический анализ выражения и проверьте наличие ошибок, но этот метод не учитывает результирующее значение. Формальные оценки будет отложен до [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) где синтаксический анализ выражения при вычислении (см. [вычисления выражения для контроля](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 [Оценки выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)