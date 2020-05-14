---
title: Оценка выражения окна смотреть (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738838"
---
# <a name="evaluate-a-watch-window-expression"></a>Оценить выражение окна часов
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 При приостановке выполнения Visual Studio вызывает движок отладки (DE) для определения текущего значения каждого выражения в списке наблюдения. DE оценивает каждое выражение с помощью оценщика выражения (EE), а Visual Studio отображает его значение в окне **Watch.**

 Ниже приводится обзор того, как оценивается выражение списка наблюдения:

1. Visual Studio вызывает [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) DE, чтобы получить контекст выражения, который может быть использован для оценки выражений.

2. Для каждого выражения в списке часов Visual Studio призывает [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) преобразовать текст выражения в разображеное выражение.

3. `IDebugExpressionContext2::ParseText`вызывает [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для того чтобы сделать фактическую работу разбора текста и произвести объект [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

4. `IDebugExpressionContext2::ParseText`создает объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и `IDebugParsedExpression` помещает объект в него. Этот`DebugExpression2` объект I затем возвращается в Visual Studio.

5. Visual Studio вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для оценки разогнанных выражений.

6. `IDebugExpression2::EvaluateSync`передает вызов [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) чтобы сделать фактическую оценку и произвести объект [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) который возвращается в Visual Studio.

7. Visual Studio вызывает [GetPropertyInfo,](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) чтобы получить значение выражения, которое затем отображается в списке часов.

## <a name="parse-then-evaluate"></a>Parse затем оценить
 Поскольку разбор сложного выражения может занять гораздо больше времени, чем его оценка, процесс оценки выражения разбит на два шага: 1) разбор выражения и 2) оценка разогнанных выражений. Таким образом, оценка может происходить много раз, но выражение должно быть разобрано только один раз. Промежуточное разображеное выражение возвращается из EE в объекте [IDebugParsedExpression,](../../extensibility/debugger/reference/idebugparsedexpression.md) который, в свою очередь, инкапсулируется и возвращается из DE в качестве объекта [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) Объект `IDebugExpression` откладывает всю оценку объекту. `IDebugParsedExpression`

> [!NOTE]
> EE не является необходимым придерживаться этого двухэтапного процесса, даже если Visual Studio предполагает это; EE может анализировать и оценивать на том же этапе, когда [называется EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (так работает образец MyCEE, например). Если ваш язык может формировать сложные выражения, вы можете отделить шаг разбора от шага оценки. Это может повысить производительность в Visual Studio отладчика, когда многие выражения смотреть в настоящее время показано.

## <a name="in-this-section"></a>В этом разделе
 [Пример реализации оценки выражений](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Использует образец MyCEE для прохождения процесса оценки выражения.

 [Оценка экспрессии часов](../../extensibility/debugger/evaluating-a-watch-expression.md) Объясняет, что происходит после успешного разбора выражения.

## <a name="related-sections"></a>См. также
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Приводит аргументы, которые передаются при вызове движка отладки (DE) оценщику выражения (EE).

## <a name="see-also"></a>См. также
 [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
