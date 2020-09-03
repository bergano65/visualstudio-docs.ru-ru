---
title: Вычисление выражений в режиме приостановки выполнения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152760"
---
# <a name="expression-evaluation-in-break-mode"></a>Вычисление выражений в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен выполнять вычисление выражений.  
  
## <a name="expression-evaluation-process"></a>Процесс оценки выражений  
 Ниже приведены основные шаги, выполняемые при вычислении выражения.  
  
1. Диспетчер отладки сеансов (SDM) вызывает [IDebugStackFrame2:: жетекспрессионконтекст](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , чтобы получить интерфейс контекста выражения, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Затем SDM вызывает [IDebugExpressionContext2::P арсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) со строкой, которую необходимо проанализировать.  
  
3. Если Парсетекст не возвращает S_OK, то возвращается причина ошибки.  
  
     ином  
  
     Если Парсетекст возвращает S_OK, то модель SDM может затем вызвать либо [IDebugExpression2:: евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , либо [IDebugExpression2:: евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , чтобы получить конечное значение из проанализированного выражения.  
  
    - В случае использования `IDebugExpression2::EvaluateSync` данный интерфейс обратного вызова используется для передачи текущего процесса оценки. Окончательное значение возвращается в интерфейсе [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - В случае использования `IDebugExpression2::EvaluateAsync` данный интерфейс обратного вызова используется для передачи текущего процесса оценки. После завершения оценки Евалуатеасинк отправляет интерфейс [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) через обратный вызов. При использовании этого интерфейса событий окончательное значение может быть получено с помощью параметра [result](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
