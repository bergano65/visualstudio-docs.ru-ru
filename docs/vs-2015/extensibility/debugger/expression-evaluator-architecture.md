---
title: Архитектура вычислителя выражений | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efb48fdc65fbc8d815c77f6e51e65312d9c93e0d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563452"
---
# <a name="expression-evaluator-architecture"></a>Архитектура вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [архитектура вычислителя выражений](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator-architecture).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Интеграция языка в пакет отладки Visual Studio означает реализация интерфейсы вычислителя (EE) требуется выражение и вызов распространенных поставщика символов с времени выполнения языка (SP) и интерфейсов связывателя. Объекты SP и связыватель, вместе с текущего адреса выполнения, являются контекст, в котором вычисляются выражения. Сведения, которые эти интерфейсы создания и использования представляет основные понятия в архитектуре EE.  
  
## <a name="overview"></a>Обзор  
  
### <a name="parsing-the-expression"></a>Синтаксический анализ выражения  
 При отладке программы, выражения вычисляются по ряду причин, но всегда при отладке программы была остановлена в точке останова (точки останова при помещении пользователем или один из-за исключения). Это в данный момент, когда Visual Studio получает кадр стека, представленные как [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, из обработчика отладки (DE). Visual Studio, затем вызывает [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс. Этот интерфейс представляет контекст, в котором выражения; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) представляет собой точку входа для ознакомления. Вплоть до этого момента все интерфейсы реализуются путем DE.  
  
 Когда `IDebugExpressionContext2::ParseText` является именем, создает DE EE, связанные с языком исходного файла, где произошла точка останова (DE также создает экземпляр SH на этом этапе). Представленный EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) интерфейс. Затем вызывает DE [проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Чтобы преобразовать выражение (в текстовой форме) проанализированное выражение, готова для оценки. Этот проанализированное выражение представлено [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) интерфейс. Обратите внимание, что выражение обычно анализируется и не оценивается на этом этапе.  
  
 DE создает объект, реализующий [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс помещает `IDebugParsedExpression` в коллекцию `IDebugExpression2` объекта и возвращает `IDebugExpression2` объекта из `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Вычисление выражения  
 Visual Studio вызывает метод [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для оценки проанализированное выражение. Оба метода вызова [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` вызывает метод немедленно, хотя `IDebugExpression2::EvaluateAsync` вызывает метод через фоновом потоке) для оценки проанализированное выражение и возврата [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет значение и тип результата разбираемого выражения. `IDebugParsedExpression::EvaluateSync` Использование предоставленного SH, адрес и привязки для преобразования проанализированное выражение в фактическое значение, представленное `IDebugProperty2` интерфейс.  
  
### <a name="for-example"></a>Например  
 После точки останова в работающей программе, пользователь выбирает просмотр переменной в **"Быстрая проверка"** диалоговое окно. Это диалоговое окно показывает имя переменной, его значение и тип. Как правило, он может изменять значение.  
  
 Когда **"Быстрая проверка"** показано диалоговое окно, имя переменной, проверяемого отправляется как текст, [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Эта команда возвращает [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект, представляющий проанализированное выражение таким образом, переменная. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) затем вызывается для создания `IDebugProperty2` объект, представляющий значение переменной и тип, а также его имя. Это это данные, которые будут отображаться.  
  
 Если пользователь изменяет значение переменной [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) вызывается с новое значение, которое изменяет значение переменной в памяти, поэтому он будет использоваться, когда программа возобновляет работу под управлением.  
  
 См. в разделе [отображение "Локальные"](../../extensibility/debugger/displaying-locals.md) Дополнительные сведения об этом процессе отображения значений переменных. См. в разделе [изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md) узнать больше о том, как изменяется значение переменной.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые во время DE вызывает EE.  
  
 [Интерфейсы вычислителя ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Описывает важные интерфейсы, необходимые при написании EE, наряду с контекстом оценки.  
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)

