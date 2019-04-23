---
title: Вычисление выражения окна контрольных значений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9fecd6960b07edb84e946899024ffbbe71bf39c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094974"
---
# <a name="evaluate-a-watch-window-expression"></a>Оценка выражения окна контрольных значений
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы определить текущее значение каждого выражения в его список наблюдения за. DE вычисляет каждое выражение, с помощью вычислителя выражений (EE) и Visual Studio отображает его значение в **Watch** окна.

 Ниже приведен обзор порядок оценки выражения контрольных значений списка.

1. Visual Studio вызывает DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения контексте выражения, который может использоваться для оценки выражений.

2. Для каждого выражения в список наблюдения за Visual Studio вызывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) преобразуемый текст выражения в проанализированное выражение.

3. `IDebugExpressionContext2::ParseText` вызовы [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для выполняют фактическую работу синтаксического анализа текста и создают [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объекта.

4. `IDebugExpressionContext2::ParseText` Создает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект и помещает `IDebugParsedExpression` объекта в него. Это я`DebugExpression2` затем восстанавливается в Visual Studio.

5. Visual Studio вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для оценки проанализированное выражение.

6. `IDebugExpression2::EvaluateSync` вызов передается [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) фактические вычисления и создают [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, возвращаемый в Visual Studio.

7. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для получения значения выражения, которое отображается в списке отслеживания.

## <a name="parse-then-evaluate"></a>Синтаксический анализ, а затем оценить
 Поскольку синтаксический анализ сложное выражение может занять гораздо больше, чем операции по оценке его, в результате вычисления выражения разбивается на два этапа: (1) синтаксический анализ выражения и 2) оценить проанализированное выражение. Таким образом, вычисление может выполняться много раз, но выражение необходимо выполнить синтаксический анализ только один раз. Промежуточные проанализированное выражение возвращается из EE в [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) объект, который в свою очередь инкапсулированы и возвращенные DE как [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта. `IDebugExpression` Объект откладывает все оценку для `IDebugParsedExpression` объекта.

> [!NOTE]
>  Это необходимо для EE придерживаться Этот двухэтапный процесс, несмотря на то, что Visual Studio предполагается, что это; EE позволяет анализировать и оценивать в одном шаге при [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) вызывается (это как работает этот пример MyCEE, например). Если ваш язык можно сформировать сложные выражения, можно разделить на этапе синтаксического анализа на этапе оценки. Это может повысить производительность в отладчике Visual Studio, когда многие просмотреть выражений появляются.

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации вычисления выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) использует выборку MyCEE для процесса вычисления выражения.

 [Вычисление выражения контрольных значений](../../extensibility/debugger/evaluating-a-watch-expression.md) объясняется, что происходит после успешной выражение синтаксического анализа.

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) предоставляет аргументы, передаваемые, когда модуль отладки (DE) вызывает средство оценки выражений (EE).

## <a name="see-also"></a>См. также
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)