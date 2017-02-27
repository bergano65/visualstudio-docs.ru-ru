---
title: "Пример реализации вычисление выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вычислители выражений"
  - "отладка [отладка SDK] вычислители выражений"
  - "вычисление выражений, примеры"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Пример реализации вычисление выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Для **Контрольные значения** окно выражение, Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта.`IDebugExpressionContext2::ParseText` Создает средство оценки выражений \(EE\) и вызывает метод [Анализ](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для получения [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
 Эта реализация `IDebugExpressionEvaluator::Parse` выполняет следующие задачи:  
  
1.  \[C\+\+\] Выполняет синтаксический анализ выражения для поиска ошибок.  
  
2.  Создает экземпляр класса \(называется `CParsedExpression` в этом примере\), реализующий `IDebugParsedExpression` интерфейса и сохраняет в классе выражение для синтаксического анализа.  
  
3.  Возвращает `IDebugParsedExpression` интерфейс из `CParsedExpression` объекта.  
  
> [!NOTE]
>  В приведенных ниже примерах в образце MyCEE, средство оценки выражений не разделения синтаксический анализ на основе оценки.  
  
## Управляемый код  
 Это реализация `IDebugExpressionEvaluator::Parse` в управляемом коде. Обратите внимание, что эта версия метода откладывает для синтаксического анализа [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) код для синтаксического анализа, оценке и в то же время \(см. [Вычисление выражения Контрольное значение](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## Неуправляемый код  
 Это реализация `IDebugExpressionEvaluator::Parse` в неуправляемом коде. Этот метод вызывает вспомогательную функцию `Parse`, выполнить синтаксический анализ выражения и проверка на наличие ошибок, но этот метод не учитывает результирующее значение. Формальные оценки будет отложен до [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) где синтаксический анализ выражения во время его оценки \(см. [Вычисление выражения Контрольное значение](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## См. также  
 [Оценки выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Вычисление выражения Контрольное значение](../../extensibility/debugger/evaluating-a-watch-expression.md)