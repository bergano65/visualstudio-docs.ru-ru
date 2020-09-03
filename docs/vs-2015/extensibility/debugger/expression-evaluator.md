---
title: Средство оценки выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152739"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Оценивающие выражения (EE) анализируют синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, что позволяет пользователю просматривать их, когда интегрированная среда разработки находится в режиме приостановки выполнения.  
  
## <a name="using-expression-evaluators"></a>Использование средств оценки выражений  
 Выражения создаются с помощью метода [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) следующим образом:  
  
1. Модуль отладки (DE) реализует интерфейс [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2. Пакет отладки получает `IDebugExpressionContext2` объект из интерфейса [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , а затем вызывает `IDebugStackFrame2::ParseText` метод для него, чтобы получить объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3. Пакет отладки вызывает метод [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или метод [евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения значения выражения. `IDebugExpression2::EvaluateAsync` вызывается из окна «Команда» или «интерпретация». Все остальные компоненты пользовательского интерфейса вызывают `IDebugExpression2::EvaluateSync` .  
  
4. Результатом вычисления выражения является объект [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , который содержит имя, тип и значение результата вычисления выражения.  
  
   Во время вычисления выражения для EE требуются сведения из компонента поставщика символов. Поставщик символов предоставляет символьную информацию, используемую для определения и понимания проанализированного выражения.  
  
   Когда асинхронное вычисление выражения завершено, асинхронное событие отправляется методом DE через диспетчер отладки сеансов (SDM) для уведомления интегрированной среды разработки о том, что вычисление выражения завершено. После завершения вычисления синхронного выражения результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метода.  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Модули отладки должны взаимодействовать с вычислителем выражений с помощью интерфейсов среды CLR. В результате средство оценки выражений, работающее с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] механизмами отладки, должно поддерживать среду CLR (полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, который является частью компонента [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>См. также:  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
