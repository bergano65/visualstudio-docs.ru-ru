---
title: Архитектура вычислителя выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fdcdfef67531af40027a2dfe8c731fe9ba5128f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-architecture"></a>Архитектура вычислителя выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Интеграция специального языка в отладочный пакет Visual Studio означает реализации интерфейсов оценки (Эстония) требуется выражение и вызова символа во время выполнения поставщик общих языка (SP) и интерфейсы связывателя. Объекты (SP2) и привязки, вместе с текущего адреса выполнения являются контекст, в котором вычисляются выражения. Данные, эти интерфейсы, создают и получают представляет основные понятия в архитектуре EE.  
  
## <a name="overview"></a>Обзор  
  
### <a name="parsing-the-expression"></a>При анализе выражения  
 При отладке программы выражения вычисляются по ряду причин, но всегда при отлаживаемой программы было остановлено в точке останова (точки останова при помещении пользователем или один вызвано исключение). Это в данный момент, когда Visual Studio получает кадр стека, представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс из модуля отладки (DE). Visual Studio вызывает [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса. Этот интерфейс представляет контекст, в котором выражения; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) — это точка входа для ознакомления. Вплоть до этого момента все интерфейсы реализуются DE.  
  
 Если `IDebugExpressionContext2::ParseText` является вызове DE создает EE, связанные с языком исходного файла, где произошло точки останова (DE также создает SH сейчас). Представленный EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейса. Затем вызывает DE [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) преобразуемое выражение (в текстовой форме) для синтаксического анализа выражения готов для оценки. Представленный этого выражения проанализированный [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейса. Обратите внимание, что выражение обычно анализируется и не оценивается на этом этапе.  
  
 DE создает объект, реализующий интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс помещает `IDebugParsedExpression` объекта в `IDebugExpression2` объекта и возвращает `IDebugExpression2` объекта из `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Вычисление выражения  
 Visual Studio вызывает либо [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для вычисления выражения проанализированный. Обе эти методы вызывают [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` вызывает метод немедленно, а `IDebugExpression2::EvaluateAsync` вызывает метод через в фоновом потоке) для вычисления выражения проанализированный и возврата [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет значение и тип выражения проанализированный. `IDebugParsedExpression::EvaluateSync` Использование предоставленного SH, адреса и привязки для преобразования выражения проанализированный в фактическое значение, представленное `IDebugProperty2` интерфейса.  
  
### <a name="for-example"></a>Например  
 После достижения точки останова в работающей программе, пользователь выбирает для просмотра переменной в **Быстрая проверка** диалоговое окно. Это диалоговое окно предназначено показывает имя переменной, значение, а его тип. Как правило, он может изменять значение.  
  
 Когда **Быстрая проверка** диалоговое окно отображается, имя переменной, проверяемого отправляется как текст, [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Возвращает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект, представляющий проанализированное выражение таким образом, переменная. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) затем вызывается для создания `IDebugProperty2` объект, представляющий значение переменной типа, а также его имя. Именно этот отображаемой информации.  
  
 Если пользователь изменяет значение переменной [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) вызывается с новое значение, которое изменяет значение переменной в памяти, поэтому оно будет использоваться, когда выполнение программы продолжается выполнение.  
  
 В разделе [отображение локальные](../../extensibility/debugger/displaying-locals.md) Дополнительные сведения об этом процессе отображения значений переменных. В разделе [изменение значения локального](../../extensibility/debugger/changing-the-value-of-a-local.md) Дополнительные сведения о том, как изменить значение переменной.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые при DE вызывает EE.  
  
 [Интерфейсы вычислителя ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Описывает важные интерфейсы, необходимые при написании EE вместе с контекстом оценки.  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)