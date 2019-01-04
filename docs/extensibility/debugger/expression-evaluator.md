---
title: Средство оценки выражений | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 5d0e356fc1683da505068899bf15e916b2bc1408
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921501"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
Вычислители выражений (EE) просмотрите синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, что позволяет им быть просмотрен пользователем, когда IDE в режиме приостановки выполнения.  
  
## <a name="use-expression-evaluators"></a>Использовать вычислители выражений  
 Выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метода, как показано ниже:  
  
1. Модуль отладки (DE) реализует [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.  
  
2. Возвращает размер пакета отладки `IDebugExpressionContext2` объекта из [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, а затем вызывает `IDebugStackFrame2::ParseText` метод его, чтобы получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта.  
  
3. Вызовы отладки пакета [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) метод или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения значения выражения. `IDebugExpression2::EvaluateAsync` вызывается из окна команд и интерпретация. Все другие компоненты пользовательского интерфейса вызывать `IDebugExpression2::EvaluateSync`.  
  
4. Результатом вычисления выражения является [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который содержит имя, тип и значение результата вычисления выражения.  
  
   Во время вычисления выражения EE требует данные из компонент поставщика символов. Поставщик символов предоставляет символические сведения, используемые для определения и понимания проанализированное выражение.  
  
   По завершении оценки асинхронное выражение асинхронного события отправляет DE через диспетчер отладки сеансов (SDM) для уведомления IDE, что вычисление выражения завершения. И, если результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метод.  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладчиков ожидать, что дает возможность общаться с средство оценки выражений, с помощью интерфейсов Common Language Runtime (CLR). Таким образом, вычислитель выражений, работающее с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчики должны поддерживать среды CLR (полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, входящий в состав из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)