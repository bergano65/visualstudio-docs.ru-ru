---
title: "Невозможно достичь блока catch, поскольку &quot;&lt;исключение&gt;&quot; обрабатывается выше в том же операторе Try | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42031"
  - "vbc42031"
helpviewer_keywords: 
  - "BC42031"
ms.assetid: 7d15597c-5988-42ea-a853-63cbf78faaf3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно достичь блока catch, поскольку &quot;&lt;исключение&gt;&quot; обрабатывается выше в том же операторе Try
Блок `Catch` в коде недоступен, так как он обрабатывается в предыдущем блоке `Try`.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42031  
  
### Исправление ошибки  
  
-   Удалите лишний оператор.  
  
## См. также  
 [Практическое руководство. Перехват исключения в Visual Basic](http://msdn.microsoft.com/ru-ru/f3063c89-d2bf-49b1-91b5-b87edfb18b95)   
 [Практическое руководство. Проверка кода с помощью блока Try…Catch в Visual Basic](http://msdn.microsoft.com/ru-ru/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Практическое руководство. Фильтрация ошибок в блоке Catch в Visual Basic](http://msdn.microsoft.com/ru-ru/85964d0a-56e7-4301-a96e-5eaea23b7b9b)   
 [Пошаговое руководство. Структурная обработка исключений \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/440da655-4b32-490b-8b16-bfe46f41fa76)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)