---
title: Средство оценки выражений | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738692"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
Оценивающие выражения (EE) анализируют синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, что позволяет пользователю просматривать их, когда интегрированная среда разработки находится в режиме приостановки выполнения.

## <a name="use-expression-evaluators"></a>Использование оценивающих выражений
 Выражения создаются с помощью метода [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) следующим образом:

1. Модуль отладки (DE) реализует интерфейс [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. Пакет отладки получает `IDebugExpressionContext2` объект из интерфейса [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , а затем вызывает `IDebugStackFrame2::ParseText` метод для него, чтобы получить объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. Пакет отладки вызывает метод [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или метод [евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения значения выражения. `IDebugExpression2::EvaluateAsync` вызывается из окна «Команда» или «интерпретация». Все остальные компоненты пользовательского интерфейса вызывают `IDebugExpression2::EvaluateSync` .

4. Результатом вычисления выражения является объект [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , который содержит имя, тип и значение результата вычисления выражения.

   Во время вычисления выражения для EE требуются сведения из компонента поставщика символов. Поставщик символов предоставляет символьную информацию, используемую для определения и понимания проанализированного выражения.

   При завершении асинхронного вычисления выражения в DE через диспетчер отладки сеансов (SDM) отправляется асинхронное событие для уведомления интегрированной среды разработки о завершении вычисления выражения. После этого результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метода.

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Модули отладки должны взаимодействовать с вычислителем выражений с помощью интерфейсов среды CLR. В результате средство оценки выражений, работающее с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизмами отладки, должно поддерживать среду CLR (полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, который является частью компонента [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>См. также раздел
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
