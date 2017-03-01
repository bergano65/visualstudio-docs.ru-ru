---
title: "Вычисление выражений (Отладка SDK для Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 68773ccac304972f4d96642a226a586d69efb783
ms.lasthandoff: 02/22/2017

---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Вычисление выражений (Отладка SDK для Visual Studio)
В режиме приостановки выполнения интегрированной среды разработки необходима возможность оценить простого выражения, включающие несколько переменных программы. Для этой цели ядро отладки (DE) должен уметь синтаксического анализа и оценки выражения, введенные в одно из окон интегрированной среды разработки.  
  
 Выражения создаются с помощью [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и являются представленного итоговый [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейса.  
  
 **IDebugExpression2** интерфейс реализуется DE и вызывает его **EvalAsync** для возврата [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейса интегрированной среды разработки, чтобы отобразить результаты вычисления выражения в Интегрированной среде разработки. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) возвращает структуру, которая может использоваться для размещения значение выражения в окно контрольного значения или в окне «Локальные».  
  
 Вызывает пакета или сеанса отладки диспетчер отладочной (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) или [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, который представляет результат вычисления. `IDebugProperty2`содержит методы, которые возвращают имя, тип и значение выражения. Эта информация отображается в окнах отладчика.  
  
## <a name="using-expression-evaluation"></a>С помощью вычисление выражений  
 Для использования вычисления выражения, необходимо реализовать [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод и все методы [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, как показано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Вычисляет выражение асинхронно.|  
|[Прерывание](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Завершает асинхронное выражение вычисления.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Вычисляет выражение синхронно.|  
  
 Синхронные и асинхронные вычисления требуют реализации [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Асинхронное выражение для вычисления требуется реализация [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Управление выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
