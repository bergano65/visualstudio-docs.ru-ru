---
title: Вычисление выражений (пакет SDK для отладки Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562215"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Анализ выражений (пакет SDK для отладки Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В режиме приостановки выполнения среда IDE должна иметь возможность оценивать простые выражения, в которых участвует несколько переменных программы. Для этого модуль отладки (DE) должен иметь возможность анализировать и оценивать выражение, введенное в одну из окон интегрированной среды разработки.  
  
 Выражения создаются с помощью метода [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и представляются результирующим интерфейсом [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
 Интерфейс **IDebugExpression2** реализуется методом de и вызывает его метод **еваласинк** для возврата интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) в интегрированную среду разработки для отображения результатов вычисления выражений в интегрированной среде разработки. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которую можно использовать для помещения значения выражения в окно контрольных значений или в окно локальных переменных.  
  
 Пакет отладки или диспетчер отладки сеансов (SDM) вызывает [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , чтобы получить интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результат вычисления. `IDebugProperty2` содержит методы, возвращающие имя, тип и значение выражения. Эти сведения отображаются в различных окнах отладчика.  
  
## <a name="using-expression-evaluation"></a>Использование вычисления выражений  
 Чтобы использовать вычисление выражений, необходимо реализовать метод [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и все методы интерфейса [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , как показано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Асинхронно вычисляет выражение.|  
|[Рвал](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает вычисление асинхронного выражения.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Синхронно вычисляет выражение.|  
  
 Для синхронных и асинхронных вычислений требуется реализация метода [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Для вычисления асинхронного выражения требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>См. также:  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
