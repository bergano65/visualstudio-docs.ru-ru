---
title: Средство оценки выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102321"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
Вычислители выражений (EE) просмотрите синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, позволяя представлены пользователю при IDE находится в режиме приостановки выполнения.  
  
## <a name="using-expression-evaluators"></a>С помощью вычислители выражений  
 Выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод следующим образом:  
  
1.  Модуль отладки (DE) реализует [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса.  
  
2.  Возвращает отладочный пакет `IDebugExpressionContext2` объекта из [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейса, а затем вызывает метод `IDebugStackFrame2::ParseText` метод ее, чтобы получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта.  
  
3.  Вызовы отладки пакета [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) метода или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) метод, чтобы получить значение выражения. `IDebugExpression2::EvaluateAsync` вызывается из окна команд и интерпретация. Все другие компоненты пользовательского интерфейса вызывать `IDebugExpression2::EvaluateSync`.  
  
4.  Результатом вычисления выражения является [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который содержит имя, тип и значение результата вычисления выражения.  
  
 Во время вычисления выражения EE требует данные из компонента поставщика символа. Символ поставщик символьных данных, используемый для определения и понимания проанализированное выражение.  
  
 По завершении вычисления выражения асинхронных асинхронного события отправленных DE диспетчера сеанса отладки (SDM) для уведомления IDE, что оценка выражения завершения. После завершения вычисления синхронной выражение, результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метод.  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ожидать, что отладчики возможность общаться с средство оценки выражений с помощью интерфейсов Common Language Runtime (CLR). В результате вычислитель выражений, работающее с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики должна поддерживать среды CLR (полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, являющейся частью из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)