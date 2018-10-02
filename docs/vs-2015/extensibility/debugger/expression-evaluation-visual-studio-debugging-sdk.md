---
title: Вычисление выражений (пакет SDK для отладки Visual Studio) | Документация Майкрософт
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
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd5fb9ac88b2535c897978cdd63f9cf0716d53a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562867"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Анализ выражений (пакет SDK для отладки Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вычисление выражений (Отладка SDK Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk).  
  
В режиме приостановки выполнения интегрированной среды разработки должен иметь возможность оценить простого выражения, включающие несколько переменных программы. Чтобы добиться этого, модуль отладки (DE) необходима возможность синтаксического анализа и вычислить это выражение, которое вводится в одно из окон интегрированной среды разработки.  
  
 Выражения создаются с помощью [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) на них метод, представленный итоговый [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс.  
  
 **IDebugExpression2** интерфейс реализуется DE и вызывает его **EvalAsync** метод для возврата [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс в интегрированную среду разработки, для отображения результаты вычисления выражения в интегрированной среде разработки. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, можно использовать для размещения значение выражения в окне контрольных значений или в окне "Локальные".  
  
 Вызывает пакет или сеанс отладки диспетчера отладочной (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет Результат вычисления. `IDebugProperty2` содержит методы, которые возвращают имя, тип и значение выражения. Эта информация отображается в окнах отладчика.  
  
## <a name="using-expression-evaluation"></a>С помощью вычисление выражений  
 Чтобы использовать вычисление выражений, необходимо реализовать [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и все методы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, как показано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Вычисляет выражение асинхронно.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет выражение в синхронном режиме.|  
  
 Синхронные и асинхронные вычисления требуют реализации [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Асинхронное выражение для вычисления требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)

