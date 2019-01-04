---
title: Вычисление выражений (пакет SDK для отладки Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd8937963175ffe0e8cadbfe2f6653b16a1f5a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888729"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Вычисление выражений (Отладка SDK для Visual Studio)
В режиме приостановки выполнения интегрированной среды разработки должны иметь простые выражения, включающие несколько переменных программы. Для выполнения их оценки, модуль отладки (DE) необходимо проанализировать и вычислить это выражение, вводимые в одно из окон интегрированной среды разработки. 
  
 Выражения создаются с помощью [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод, а полученный в результате [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс.  
  
 **IDebugExpression2** интерфейс реализуется DE и вызывает его **EvalAsync** метод для возврата [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс в интегрированную среду разработки, для отображения результаты вычисления выражения в интегрированной среде разработки. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которая используется для помещения значение выражения в **Watch** окно или в **"Локальные"** окна.  
  
 Вызывает пакет или сеанс отладки диспетчера отладочной (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет Результат вычисления. `IDebugProperty2` содержит методы, которые возвращают имя, тип и значение выражения. Эта информация отображается в окнах отладчика.  
  
## <a name="using-expression-evaluation"></a>С помощью вычисление выражений  
 Чтобы использовать вычисление выражений, необходимо реализовать [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и все методы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, как показано в следующей таблице.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Вычисляет выражение асинхронно.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет выражение в синхронном режиме.|  
  
 Синхронные и асинхронные вычисления требуют реализации [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Асинхронное выражение для вычисления требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение управления и состояние оценки](../../extensibility/debugger/execution-control-and-state-evaluation.md)