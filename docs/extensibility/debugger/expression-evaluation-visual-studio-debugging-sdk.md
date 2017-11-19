---
title: "Вычисление выражений (Отладка пакета SDK для Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c66a6eac74b3d1494a1e98bcb95112c43c4c1bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Вычисление выражений (Отладка пакета SDK для Visual Studio)
В режиме приостановки выполнения интегрированной среды разработки необходима возможность оценить простого выражения, включающие несколько переменных программы. Для этого модуля отладки (DE) необходимо для синтаксического анализа и оценки выражения, введенные в одно из окон интегрированной среды разработки.  
  
 Выражения создаются с помощью [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и являются представленный итоговый [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейса.  
  
 **IDebugExpression2** интерфейс реализуется DE и вызывает его **EvalAsync** метод для возврата [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс IDE, для отображения результаты вычисления выражения в Интегрированной среде разработки. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которая может использоваться для размещения значение выражения в окне контрольных значений или в окне «Локальные».  
  
 Пакет или сеанс отладки диспетчер отладочной (SDM) вызывает [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет Результат вычисления. `IDebugProperty2`содержит методы, которые возвращают имя, тип и значение выражения. Эта информация отображается в окнах отладчика.  
  
## <a name="using-expression-evaluation"></a>С помощью вычисление выражений  
 Чтобы использовать вычисление выражений, необходимо реализовать [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и все методы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, как показано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет выражение.|  
|[Прерывание](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет выражение в синхронном режиме.|  
  
 Синхронные и асинхронные вычисления требуют реализацию [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Асинхронное выражение для вычисления требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)