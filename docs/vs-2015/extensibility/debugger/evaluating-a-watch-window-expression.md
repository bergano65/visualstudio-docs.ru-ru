---
title: Вычисление выражения окна контрольных значений | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4dc9a56927ebe1e7b962ab815eb34028ba75350c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801480"
---
# <a name="evaluating-a-watch-window-expression"></a>Вычисление выражения окна контрольных значений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы определить текущее значение каждого выражения в его список наблюдения за. DE вычисляет каждое выражение, с помощью вычислителя выражений (EE) и Visual Studio отображает его значение в **Watch** окна.  
  
 Ниже приведен обзор порядок оценки выражения список контрольных значений:  
  
1.  Visual Studio вызывает DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения контексте выражения, который может использоваться для оценки выражений.  
  
2.  Для каждого выражения в список наблюдения за Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) преобразуемый текст выражения в проанализированное выражение.  
  
3.  `IDebugExpressionContext2::ParseText` вызовы [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для выполняют фактическую работу синтаксического анализа текста и создают [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.  
  
4.  `IDebugExpressionContext2::ParseText` Создает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект и помещает `IDebugParsedExpression` объекта в него. Это я`DebugExpression2` затем восстанавливается в Visual Studio.  
  
5.  Visual Studio вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для оценки проанализированное выражение.  
  
6.  `IDebugExpression2::EvaluateSync` вызов передается [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) фактические вычисления и создают [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый в Visual Studio.  
  
7.  Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для получения значения выражения, которое отображается в списке отслеживания.  
  
## <a name="parse-then-evaluate"></a>Синтаксический анализ, а затем оценить  
 Поскольку синтаксический анализ сложное выражение может занять гораздо больше, чем операции по оценке его, в результате вычисления выражения разбивается на два этапа: (1) синтаксический анализ выражения и (2) оценить проанализированное выражение. Таким образом, вычисление может выполняться много раз, но выражение необходимо выполнить синтаксический анализ только один раз. Промежуточные проанализированное выражение возвращается из EE в [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объект, который в свою очередь инкапсулированы и возвращенные DE как [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта. `IDebugExpression` Объект откладывает все оценку для `IDebugParsedExpression` объекта.  
  
> [!NOTE]
>  Это необходимо для EE придерживаться Этот двухэтапный процесс, несмотря на то, что Visual Studio предполагается, что это; EE позволяет анализировать и оценивать в одном шаге при [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вызывается (это как работает этот пример MyCEE, например). Если ваш язык можно сформировать сложные выражения, можно разделить на этапе синтаксического анализа на этапе оценки. Это может повысить производительность в отладчике Visual Studio, когда многие просмотреть выражений появляются.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Использует образец MyCEE для процесса вычисления выражения.  
  
 [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Объясняет, что происходит после успешной выражение синтаксического анализа.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые, когда модуль отладки (DE) вызывает средство оценки выражений (EE).  
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

