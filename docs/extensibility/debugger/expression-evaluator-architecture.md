---
title: "Архитектура вычислителя выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Архитектура вычислители выражений"
  - "вычислители выражений, архитектура"
  - "отладка [отладка SDK] вычислители выражений"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Архитектура вычислителя выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Интеграция специального языка в отладочный пакет Visual Studio означает реализации интерфейсов оценки \(EE\) требуется выражение и вызывая символов во время выполнения поставщик общих языка \(SP\) и интерфейсы привязки. SP и привязки объектов вместе с текущего адреса выполнения — это контекст, в котором вычисляются выражения. Сведения, эти интерфейсы, создания и использования представляет основные понятия в архитектуре EE.  
  
## Обзор  
  
### Синтаксический анализ выражения  
 При отладке программы выражения оцениваются по ряду причин, но всегда при отлаживаемой программы был остановлен в точке останова \(точки останова при помещении пользователем или один вызвано исключение\). Это в данный момент, когда Visual Studio получает кадр стека, представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс из ядра отладки \(DE\). Visual Studio вызывает [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса. Этот интерфейс представляет контекст, в котором выражения; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) является точкой входа для ознакомления с программным обеспечением. Вплоть до этого момента все интерфейсы реализуются DE.  
  
 При `IDebugExpressionContext2::ParseText` является именем, создает DE EE, связанные с языком исходного файла, где произошло точки останова \(DE также создает SH сейчас\). Представленный EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейса. Затем вызывает DE [Анализ](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для преобразования выражений \(в текстовой форме\) проанализированное выражение, готова для оценки. Этот проанализированный выражение представлено [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейса. Обратите внимание, что выражение обычно анализируется и не оценивается на этом этапе.  
  
 DE создает объект, реализующий интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс помещает `IDebugParsedExpression` объекта в `IDebugExpression2` объекта и возвращает `IDebugExpression2` объекта из `IDebugExpressionContext2::ParseText`.  
  
### Оценка выражения  
 Visual Studio вызывает либо [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) проанализированного выражения. Оба эти метода вызова [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` вызывает метод немедленно, а `IDebugExpression2::EvaluateAsync` вызывает метод через в фоновом потоке\) для оценки проанализированное выражение и возвращают [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий значение и тип проанализированное выражение.`IDebugParsedExpression::EvaluateSync` Использование предоставленного SH, адрес и привязки для преобразования проанализированное выражение в фактическое значение, представленное `IDebugProperty2` интерфейса.  
  
### Например  
 После достижения точки останова в работающей программе, пользователь выбирает просмотр переменной в **Быстрая проверка** диалоговое окно. Этом диалоговом окне отображается имя переменной, значение и тип. Пользователь обычно можно изменить значение.  
  
 Когда **Быстрая проверка** показано диалоговое окно, имя переменной, проверяемая отправляется как текст, чтобы [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Этот метод возвращает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект, представляющий проанализированное выражение в этом случае, переменная.[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) Затем вызывается для создания `IDebugProperty2` объект, представляющий значение переменной типа, а также его имя. Именно этот отображаемой информации.  
  
 Если пользователь изменяет значение переменной [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) вызывается с новым значением, который изменяет значение переменной в памяти, оно будет использоваться, когда выполнение программы продолжается выполнение.  
  
 В разделе [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) Дополнительные сведения об этом процессе для отображения значений переменных. В разделе [Изменение значения локальной](../../extensibility/debugger/changing-the-value-of-a-local.md) Дополнительные сведения о том, как изменяется значение переменной.  
  
## Содержание  
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые при вызове DE EE.  
  
 [Интерфейсы вычислителя выражения ключа](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Описывает важные интерфейсы, необходимые при написании EE, вместе с контекстом оценки.  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [Изменение значения локальной](../../extensibility/debugger/changing-the-value-of-a-local.md)