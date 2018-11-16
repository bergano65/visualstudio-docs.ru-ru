---
title: Вычисление выражений в режиме приостановки выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5b307dead1d2fb193f7d34b28ef4eaec11c6dad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728992"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и следует проводить вычисления выражения.  
  
## <a name="expression-evaluation-process"></a>Процесс оценки выражения  
 Ниже приведены основные шаги, участвующих в вычислении выражения.  
  
1.  Диспетчер отладки сеансов (SDM) вызывает [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) получить интерфейс контекста выражения [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Затем вызывает SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой, чтобы выполнить синтаксический анализ.  
  
3.  Если ParseText не возвращает значение S_OK, возвращается причина ошибки.  
  
     -в противном случае —  
  
     Если ParseText возвращает S_OK, SDM может затем вызвать либо метод [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения окончательного значения из проанализированное выражение.  
  
    -   В случае с помощью `IDebugExpression2::EvaluateSync`, интерфейс заданного обратного вызова используется для связи непрерывный процесс оценки. Конечное значение возвращается в [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс.  
  
    -   В случае с помощью `IDebugExpression2::EvaluateAsync`, интерфейс заданного обратного вызова используется для связи непрерывный процесс оценки. По завершении оценки EvaluateAsync отправляет [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейса через обратный вызов. С помощью этого интерфейса событий, конечное значение можно получить с помощью [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

