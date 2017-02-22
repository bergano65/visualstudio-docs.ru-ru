---
title: "Вычислитель выражений | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "выражения [пакет SDK для отладки]"
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Вычислитель выражений
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вычислителя выражений \(EE\) проверяет синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, позволяя их для просмотра пользователь, когда интегрированная среда разработки в режиме приостановки выполнения.  
  
## С помощью средства оценки выражений  
 Выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод следующим образом:  
  
1.  Отладчик \(DE\) реализует IDebugExpressionContext2 интерфейс.  
  
2.  Пакет отладки возвращает `IDebugExpressionContext2` объект  [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс и затем вызывает метод  `IDebugStackFrame2::ParseText` метод на нем для получения  [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объект.  
  
3.  Пакет отладки вызывает [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) метод или  [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) метод, чтобы получить значение выражения.  `IDebugExpression2::EvaluateAsync` вызывает метод из команды или окна интерпретации.  Все остальные вызов компонентов пользовательского интерфейса `IDebugExpression2::EvaluateSync`.  
  
4.  Результат оценки выражений IDebugProperty2 объект, содержащий имя, тип и значение результата вычисления выражения.  
  
 Во время оценки выражения, EE требует данные из компонента поставщика символов.  Предоставляемый поставщиком символов символьные данные, используемые для идентификации и понимание проанализированное выражение.  
  
 Когда асинхронная завершения асинхронное вычисление выражений событие отправляется DE через сеанс отладки \(SDM\) диспетчер для уведомления среды разработки, что вычисление выражений завершена.  После завершения синхронной вычисление выражений результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метод.  
  
## Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка обработчики рассчитывайте разговаривать с средство оценки выражений с помощью интерфейсов среды CLR.  В результате средство оценки выражений, которое работает с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обработчики поддержки отладки среды CLR \(полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, часть  [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]\).  
  
## См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)