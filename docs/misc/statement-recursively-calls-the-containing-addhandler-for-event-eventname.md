---
title: "Оператор рекурсивно вызывает вмещающий AddHandler для события события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор рекурсивно вызывает вмещающий AddHandler для события события &quot;&lt;имя_события&gt;&quot;
Операторы в методе доступа `AddHandler` определения события не должны ссылаться на событие напрямую.  
  
 Рекомендуется хранить список обработчиков событий как закрытое поле в классе, структуре или модуле, определяющем событие. Дополнительные сведения см. в разделах [Практическое руководство. Объявление пользовательских событий для предотвращения блокировки](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) и [Практическое руководство. Объявление пользовательских событий для экономии памяти](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md).  
  
 **Идентификатор ошибки:** BC41998  
  
### Исправление ошибки  
  
-   Перепишите определение события, чтобы избежать рекурсии.  
  
## См. также  
 [AddHandler — удалить](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Практическое руководство. Объявление пользовательских событий для предотвращения блокировки](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Практическое руководство. Объявление пользовательских событий для экономии памяти](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)