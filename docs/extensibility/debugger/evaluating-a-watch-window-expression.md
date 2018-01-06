---
title: "Оценки выражения окна контрольных значений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb109fd91e4c295bf372b14e26bc2a75c3be6b1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-a-watch-window-expression"></a>Оценки выражения окна контрольных значений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы определить текущее значение каждого выражения в списке контрольных значений. DE вычисляет каждое выражение, с помощью вычислитель выражений (EE) и Visual Studio отображает его значение в **Контрольные значения** окна.  
  
 Ниже приведен обзор порядок оценки контрольного списка выражения:  
  
1.  Visual Studio вызывает DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения контексте выражения, который может использоваться для вычисления выражений.  
  
2.  Для каждого выражения в списке отслеживания Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для преобразования текста выражения в разбираемого выражения.  
  
3.  `IDebugExpressionContext2::ParseText`вызовы [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) делать фактические трудозатраты синтаксического анализа текста и создают [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
4.  `IDebugExpressionContext2::ParseText`Создает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта и помещает `IDebugParsedExpression` объекта в него. Это я`DebugExpression2` объект возвращается в Visual Studio.  
  
5.  Visual Studio вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для вычисления выражения проанализированный.  
  
6.  `IDebugExpression2::EvaluateSync`вызов передается [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) сделать фактическое оценки и создания [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый в Visual Studio.  
  
7.  Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , чтобы получить значение выражения, которое отображается в списке отслеживания.  
  
## <a name="parse-then-evaluate"></a>Синтаксический анализ, а затем вычислить  
 Поскольку синтаксический анализ сложное выражение может занять гораздо больше, чем операции по оценке его, в результате вычисления выражения разбивается на два шага: (1) синтаксический анализ выражения и (2) вычислить значение выражения проанализированный. Таким образом, вычисление может выполняться много раз, но выражение необходимо проанализировать только один раз. Возвращенный промежуточного выражения проанализированный EE в [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объект, который в свою очередь, содержащийся и возвращенные DE как [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта. `IDebugExpression` Объекта откладывает все оценку для `IDebugParsedExpression` объекта.  
  
> [!NOTE]
>  Это необходимо для EE соответствовать это двухэтапный процесс, несмотря на то, что Visual Studio предполагается позволяет анализировать и оценивать в одном шаге EE при [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вызывается (это принцип работы образца MyCEE, например). Если ваш язык можно сформировать сложные выражения, можно разделить на этапе синтаксического анализа на этапе оценки. Это может повысить производительность в отладчике Visual Studio, если многие контрольных выражений появляются.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 В образце MyCEE использует для процесса вычисления выражения.  
  
 [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Объясняет, что происходит после анализа успешно выражения.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, переданные при вызове подсистемой отладки (DE) вычислитель выражений (EE).  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)