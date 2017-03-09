---
title: "Модификатор Custom недопустим в событиях, объявленных в интерфейсах. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модификатор Custom недопустим в событиях, объявленных в интерфейсах.
Настраиваемое событие не может объявляться в интерфейсе, поскольку настраиваемое событие должно предоставлять реализацию его методов `AddHandler`, `RemoverHandler` и `RaiseEvent`.  
  
 Ключевое слово `Custom` может использоваться в производном классе, который реализует это событие.  
  
 **Идентификатор ошибки:** BC31121  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Custom` из объявления события в интерфейсе.  
  
## Пример  
 В этом примере показан способ реализации события, объявленного в интерфейсе в качестве настраиваемого события.  
  
 [!CODE [VbVbalrEventError#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#3)]  
  
## См. также  
 [Custom — удалить](http://msdn.microsoft.com/ru-ru/dc62be07-c896-4866-a533-982a661d143f)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)