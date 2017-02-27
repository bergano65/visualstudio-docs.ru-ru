---
title: "Контекст вычисления выражения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "вычисление выражений, контекст"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Контекст вычисления выражения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IN [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка контекст оценки выражений.  
  
-   Представляет контекст для оценки выражений.  Как правило, контекст оценки соответствует лексической области, в которой вычислить переменные, параметры функций и методов.  Например, контекст оценки выражений предоставляет контекст, связанный с данным кадром стека для оценки локальных переменных, параметров метода и членов класса \(если применимо\).  
  
-   Возникает, когда программа остановлена в точке останова.  Выражение само структура данных, представляющий проанализированное выражение, которое готово для привязки и оценки в пределах заданного контекста.  
  
     Более подробно выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод.  При вычислении выражения, оно приводит непечатаемым строку, содержащую имя и тип переменной или аргумента и его значение.  Эта строка выводится в окне контрольных значений или в окне локальные переменные среды разработки.  
  
     Заданное a `BSTR` и  [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс обработчик отладки \(DE\) может создать  [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем синтаксического анализа выражения.  Конкретной `IDebugExpression2` интерфейс DE может получить значение с помощью синхронную и асинхронную оценки выражений.  Это значение вместе с именем и типом переменной или аргумента, отправляется в интегрированной среде разработки для отображения.  
  
## См. также  
 [Интерфейсы вычисление выражений](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)