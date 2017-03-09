---
title: "Метод RaiseEvent должен иметь такую же сигнатуру, как и делегируемый тип содержащего его события &quot;&lt;сигнатура&gt;&quot;. | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод RaiseEvent должен иметь такую же сигнатуру, как и делегируемый тип содержащего его события &quot;&lt;сигнатура&gt;&quot;.
Объявление `Custom Event` должно иметь объявление `RaiseEvent` с той же сигнатурой, что и у типа делегата, заданного предложением `As` пользовательского события.  
  
 Для совпадения сигнатур объявление `RaiseEvent` и делегат должны иметь совпадающее число параметров и типы параметров.  
  
 **Идентификатор ошибки:** BC31137  
  
### Исправление ошибки  
  
-   Измените параметры объявления `RaiseEvent` так, чтобы они соответствовали параметрам типа делегата.  
  
## Пример  
 В этом примере показано пользовательское событие с корректными типами параметров для объявления `RaiseEvent`.  
  
 [!CODE [VbVbalrEventError#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#2)]  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [RaiseEvent](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)