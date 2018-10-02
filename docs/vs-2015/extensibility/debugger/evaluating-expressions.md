---
title: Вычисление выражений | Документация Майкрософт
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
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c51cc08da8c71a2ac1f25d02461ea9c24797ebc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568569"
---
# <a name="evaluating-expressions"></a>Вычисление выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [оценки выражения](https://docs.microsoft.com/visualstudio/extensibility/debugger/evaluating-expressions).  
  
Выражения создаются на основе строки, переданные с "Видимые", Контрольные значения, Быстрая проверка или немедленного windows. При вычислении выражения, он создает строку печати, которая содержит имя и тип переменной или аргумента и его значение. Эта строка отображается в соответствующем окне интегрированной среды разработки.  
  
## <a name="implementation"></a>Реализация  
 Выражения вычисляются в том случае, если программа остановлена в точке останова. Представленный самого выражения [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, которое будет готов для привязки и оценки в контекст оценки данного выражения. Определяет, кадр стека контекста вычисления выражений, предоставляющего модуль отладки (DE), реализовав [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.  
  
 Учитывая строку пользователя и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса модуля отладки (DE) можно получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем передачи строки пользователя к [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. Возвращаемый интерфейс IDebugExpression2 содержится проанализированное выражение для оценки готовности.  
  
 С помощью `IDebugExpression2` интерфейс, DE можно получить значение выражения по синхронным или асинхронным выражениям, с помощью [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения. Значение, имя и тип представлены [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс.  
  
 Чтобы включить вычисление выражений, необходимо реализовать DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейсов. Синхронные и асинхронные вычисления требуют реализации [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)

