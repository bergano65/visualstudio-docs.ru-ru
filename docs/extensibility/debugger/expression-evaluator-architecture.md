---
title: Архитектура оценки экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738694"
---
# <a name="expression-evaluator-architecture"></a>Архитектура оценки экспрессии
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Интеграция несвободного языка в пакет отладки Visual Studio означает, что необходимо настроить интерфейсы требуемого оценщика выражения (EE) и вызвать интерфейсы символов общего времени выполнения языка (SP) и интерфейсы связующего. Объекты SP и связующего, а также текущий адрес выполнения являются контекстом, в котором оцениваются выражения. Информация, которую эти интерфейсы производят и потребляют, представляет ключевые понятия в архитектуре EE.

## <a name="overview"></a>Обзор

### <a name="parse-the-expression"></a>Парс выражение
 При отладке программы выражения оцениваются по ряду причин, но всегда, когда отладка программы была остановлена в точке разрыва (либо точка разрыва, размещенная пользователем, либо точка разрыва, вызванная исключением). Именно в этот момент Visual Studio получает стек кадра, представленного интерфейсом [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) от отладки двигателя (DE). Visual Studio затем вызывает [GetExpressionContext,](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) чтобы получить интерфейс [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Этот интерфейс представляет собой контекст, в котором выражения могут быть оценены; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) является точкой входа в процесс оценки. До этого момента все интерфейсы реализуются DE.

 Когда `IDebugExpressionContext2::ParseText` вызов называется, DE мгновенно eE, связанный с языком исходного файла, где произошла точка разрыва (DE также мгновенно вызывает SH в этой точке). EE представлен интерфейсом [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) DE затем вызывает [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для преобразования выражения (в текстовой форме) в разображеное выражение, готовое к оценке. Это разогнанные выражения представлены интерфейсом [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) Выражение обычно разбирается и не оценивается в этой точке.

 DE создает объект, который реализует интерфейс [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugParsedExpression` помещает `IDebugExpression2` объект в `IDebugExpression2` объект `IDebugExpressionContext2::ParseText`и возвращает объект из.

### <a name="evaluate-the-expression"></a>Оценка выражения
 Visual Studio вызывает либо [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для оценки разогнанных выражений. Оба этих метода вызывают`IDebugExpression2::EvaluateSync` [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (вызывает `IDebugExpression2::EvaluateAsync` метод немедленно, в то время как вызывает метод через фоновый поток) для оценки разобранного выражения и возвращения интерфейса [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) который представляет значение и тип разобранного выражения. `IDebugParsedExpression::EvaluateSync`использует поставляемый SH, адрес и связующее значение для преобразования разображенные выражения в реальное значение, представленное интерфейсом. `IDebugProperty2`

### <a name="for-example"></a>Например.
 После того, как точка разрыва попала в запущенную программу, пользователь выбирает для просмотра переменной в диалоговом поле **quickWatch.** В этом диалоговом поле отображается имя переменной, ее значение и ее тип. Пользователь обычно может изменить значение.

 При отображечном диалоговом поле **«Быстрый смотреть»** имя исследуемой переменной отправляется в виде текста [в ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Это возвращает объект [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) представляющий разогнанный выражение, в данном случае переменную. [Затем EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) вызывается `IDebugProperty2` для создания объекта, представляющего значение и тип переменной, а также ее имя. Именно эта информация отображается.

 Если пользователь изменяет значение переменной, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) вызывается с новым значением, которое изменяет значение переменной в памяти, поэтому оно будет использоваться при возобновлении работы программы.

 Более подробную информацию об этом процессе отображения значений переменных можно [просмотреть.](../../extensibility/debugger/displaying-locals.md) Подробнее об изменении значения переменной можно на [см.](../../extensibility/debugger/changing-the-value-of-a-local.md)

## <a name="in-this-section"></a>В этом разделе
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Предоставляет аргументы, которые передаются, когда DE вызывает EE.

 [Интерфейсы оценщика ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Описывает важнейшие интерфейсы, необходимые при написании EE, наряду с контекстом оценки.

## <a name="see-also"></a>См. также
- [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md)
- [Изменение ценности локального](../../extensibility/debugger/changing-the-value-of-a-local.md)
