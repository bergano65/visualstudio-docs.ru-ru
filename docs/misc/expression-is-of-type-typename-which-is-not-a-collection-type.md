---
title: "Выражение имеет тип &quot;&lt;имя_типа&gt;&quot;, не являющийся коллекцией | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение имеет тип &quot;&lt;имя_типа&gt;&quot;, не являющийся коллекцией
Переменная группы, указанная в операторе `For Each`, не является объектом коллекции или массивом, а ее тип не реализует интерфейс <xref:System.Collections.IEnumerable>. Тип должен либо поддерживать шаблон разработки коллекции [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], либо реализовывать интерфейс <xref:System.Collections.IEnumerable>.  
  
 **Идентификатор ошибки:** BC32023  
  
### Исправление ошибки  
  
-   Объявите переменную группы как имеющую тип класса, который либо поддерживает шаблон разработки коллекции [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], либо реализует интерфейс <xref:System.Collections.IEnumerable>.  
  
## См. также  
 <xref:System.Collections.IEnumerable>   
 [Оператор For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Класс Collection в Visual Basic](http://msdn.microsoft.com/ru-ru/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)