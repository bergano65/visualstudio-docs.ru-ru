---
title: Оценка экспрессии Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738692"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
Оценки экспрессии (EE) изучают синтаксис языка для разбора и оценки переменных и выражений во время выполнения, что позволяет просматривать их пользователю, когда IDE находится в режиме перерыва.

## <a name="use-expression-evaluators"></a>Использование оценщиков выражений
 Выражения создаются с помощью метода [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) следующим образом:

1. Отладка двигателя (DE) реализует интерфейс [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Пакет отладки `IDebugExpressionContext2` получает объект из интерфейса [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) а затем вызывает `IDebugStackFrame2::ParseText` метод на нем, чтобы получить объект [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. Пакет отладки вызывает метод [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или метод [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения значения выражения. `IDebugExpression2::EvaluateAsync`вызывается из окна Командования/Немедленного. Все остальные компоненты `IDebugExpression2::EvaluateSync`uI вызываются .

4. Результатом оценки выражения является объект [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) содержащий имя, тип и значение результата оценки выражения.

   Во время оценки выражения EE требуется информация от компонента поставщика символов. Поставщик символов предоставляет символическую информацию, используемую для идентификации и понимания разогнанных выражений.

   Когда асинхронная оценка выражения завершается, асинхронное событие отправляется DE через диспетчера отладки сеанса (SDM), чтобы уведомить IDE о завершении оценки выражения. И, результат оценки затем возвращается из `IDebugExpression2::EvaluateSync` вызова в метод.

## <a name="implementation-notes"></a>Примечания по реализации
 Двигатели [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки рассчитывают поговорить с оценщиком выражения с помощью интерфейсов Common Language Runtime (CLR). В результате, оценщик выражения, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] который работает с двигателями отладки, должен поддерживать CLR (полный список всех интерфейсов отладки CLR можно найти в debugref.doc, который является частью [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).

## <a name="see-also"></a>См. также
- [Компоненты debugger](../../extensibility/debugger/debugger-components.md)
