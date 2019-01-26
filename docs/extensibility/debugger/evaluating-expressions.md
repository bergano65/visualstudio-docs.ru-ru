---
title: Вычисление выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41e56368497d3a8058437ea726488874081f4d45
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069756"
---
# <a name="evaluate-expressions"></a>Вычисление выражений
Выражения создаются на основе строк, переданные с **"Видимые"**, **Watch**, **"Быстрая проверка"**, или **Интерпретация** windows. При вычислении выражения, он создает строку печати, которая содержит имя и тип переменной или аргумента и его значение. Эта строка отображается в соответствующем окне интегрированной среды разработки.  
  
## <a name="implementation"></a>Реализация  
 Выражения вычисляются в том случае, если программа остановлена в точке останова. Представленный самого выражения [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, которое будет готов для привязки и оценки в контекст оценки данного выражения. Определяет, кадр стека контекста вычисления выражений, предоставляющего модуль отладки (DE), реализовав [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.  
  
 Учитывая строку пользователя и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса модуля отладки (DE) можно получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем передачи строки пользователя к [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. Возвращаемый интерфейс IDebugExpression2 содержит готова для оценки проанализированное выражение.  
  
 С помощью `IDebugExpression2` интерфейс, DE можно получить значение выражения по синхронным или асинхронным выражениям, с помощью [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения. Значение, имя и тип представлены [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс.  
  
 Чтобы включить вычисление выражений, необходимо реализовать DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейсов. Синхронные и асинхронные вычисления требуют реализации [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)   
 [Отладка задач](../../extensibility/debugger/debugging-tasks.md)