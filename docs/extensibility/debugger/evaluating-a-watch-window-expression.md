---
title: "Оценки выражения окна контрольных значений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Выражения окна контрольных значений"
  - "Окно контрольного значения, выражения"
  - "Вычисление выражения, выражения окна контрольных значений"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Оценки выражения окна контрольных значений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда выполнение приостанавливается, Visual Studio вызывает отладчик \(DE\), чтобы определить текущее значение каждого выражения в списке Контрольное значение. DE вычисляет каждое выражение, с помощью вычислитель выражений \(EE\) и Visual Studio отображает его значение в **Контрольные значения** окна.  
  
 Ниже приведен обзор проверка контрольного списка выражения:  
  
1.  Visual Studio вызывает DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения контекста выражения, который может использоваться для вычисления выражений.  
  
2.  Для каждого выражения в списке отслеживания Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для преобразования текста выражения в проанализированное выражение.  
  
3.  `IDebugExpressionContext2::ParseText` вызовы [Анализ](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) делать фактические трудозатраты синтаксического анализа текста и создают [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
4.  `IDebugExpressionContext2::ParseText` Создает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта и помещает `IDebugParsedExpression` объект в его. Это я`DebugExpression2` объект возвращается Visual Studio.  
  
5.  Visual Studio вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) проанализированного выражения.  
  
6.  `IDebugExpression2::EvaluateSync` вызов передается [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Фактическое оценки и создания [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый в Visual Studio.  
  
7.  Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для получения значения выражения, которое отображается в списке отслеживания.  
  
## Синтаксический анализ и оценка  
 Синтаксический анализ сложных выражений может занять значительно больше времени, чем его вычисление, в результате вычисления выражения разбивается на два этапа: 1\) синтаксический анализ выражения и \(2\) оценить проанализированное выражение. Таким образом, оценка может происходить много раз, но выражение необходимо проанализировать только один раз. Промежуточные проанализированное выражение возвращается из EE в [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объект, который в свою очередь инкапсулируются и возвращенные DE как [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект.`IDebugExpression` Объект\-откладывает все оценку для `IDebugParsedExpression` объекта.  
  
> [!NOTE]
>  Это необходимо для EE придерживаться такой двухступенчатый процесс, несмотря на то, что Visual Studio предполагается следующее: EE можно проанализировать и оценить на том же этапе при [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вызывается \(это принцип работы образца MyCEE, например\). Если язык можно сформировать сложные выражения, можно разделить на этапе синтаксического анализа на этапе оценки. Это может повысить производительность в отладчике Visual Studio, когда многие контрольных выражений появляются.  
  
## Содержание  
 [Пример реализации вычисление выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Образец MyCEE использует для пошагового вычисления выражения.  
  
 [Вычисление выражения Контрольное значение](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Объясняется, что происходит после обработки успешного выражение.  
  
## Связанные разделы  
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые при вызове подсистемой отладки \(DE\), средство оценки выражений \(EE\).  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)