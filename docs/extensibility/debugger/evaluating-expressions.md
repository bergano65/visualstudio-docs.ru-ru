---
title: "Вычисление выражений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Оценка выражения [пакет SDK для отладки],"
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Вычисление выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Выражения создаются из строк, переданных вниз от видимые, контрольные значения и быстрая проверка, непосредственных windows.  При вычислении выражения, оно приводит непечатаемым строку, содержащую имя и тип переменной или аргумента и его значение.  Эта строка отображается в соответствующем окне среды разработки.  
  
## Реализация  
 Выражения вычисляются когда программа остановлена в точке останова.  Выражение само представлено  IDebugExpression2 интерфейс, представляющий проанализированное выражение, которое готово для привязки и вычислений в пределах заданного контекста вычисления выражений.  Кадр стека, указывающее контекст оценки выражений, который предоставляет механизма отладки \(DE\) путем реализации IDebugExpressionContext2 интерфейс.  
  
 Если пользователю строку и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс обработчик отладки \(DE\) может получать  [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, передавая строку пользователя  [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод.  Возвращенный интерфейс IDebugExpression2 содержащий проанализированное выражение готово для оценки.  
  
 с `IDebugExpression2` интерфейс DE может получить значение выражения по синхронную и асинхронную оценки выражений, использование  [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) OR  [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  Это значение вместе с именем и типом переменной или аргумента, отправляется в интегрированной среде разработки для отображения.  Значение, имя и тип представлены IDebugProperty2 интерфейс.  
  
 Чтобы включить оценки выражений, должен реализовывать DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) и  [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейсы.  Асинхронное вычисление и параллельная и требует реализации [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.  
  
## См. также  
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Контекст вычисления выражения](../../extensibility/debugger/expression-evaluation-context.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)