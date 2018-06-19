---
title: Вычисление выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102796"
---
# <a name="evaluating-expressions"></a>Вычисление выражений
Выражения создаются из строк, которые наследуются от видимые, Контрольные значения, Быстрая проверка или немедленного windows. При вычислении выражения создает печатных строка, содержащая имя и тип переменной или аргумента, а его значение. Эта строка отображается в соответствующее окно интегрированной среды разработки.  
  
## <a name="implementation"></a>Реализация  
 Выражения вычисляются в том случае, когда остановлено в точке останова. Само выражение представленного [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, которое будет готов для привязки и оценки в контексте вычисления данного выражения. Кадр стека определяет контекст оценки выражения, предоставляющего модуль отладки (DE), реализовав [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса.  
  
 Заданной пользователем строке и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса модуля отладки (DE) можно получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, передав строку для пользователя [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. Возвращаемый интерфейс IDebugExpression2 содержит проанализированное выражение для оценки готовности.  
  
 С `IDebugExpression2` интерфейса, DE можно получить значение выражения через вычисление выражений синхронные или асинхронные, с помощью [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения. Значение, имя и тип представляются [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейса.  
  
 Чтобы включить вычисление выражений, необходимо реализовать DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейсов. Синхронные и асинхронные вычисления требуют реализацию [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Контекст оценки выражения](../../extensibility/debugger/expression-evaluation-context.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)