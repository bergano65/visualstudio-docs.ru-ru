---
title: "Операнд &quot;Using&quot; типа &quot;&lt;имя_типа&gt;&quot; должен реализовывать System.IDisposable. | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операнд &quot;Using&quot; типа &quot;&lt;имя_типа&gt;&quot; должен реализовывать System.IDisposable.
Инструкция `Using` указывает ресурс типа, который не реализует интерфейс <xref:System.IDisposable>.  
  
 Целью блока `Using` является обеспечение освобождения системного ресурса при выходе из блока. Для выполнения этой цели ресурс должен предоставлять метод <xref:System.IDisposable.Dispose%2A>, реализованный из <xref:System.IDisposable>.  
  
 **Идентификатор ошибки:** BC36010  
  
### Исправление ошибки  
  
-   Удалите этот ресурс из списка ресурсов инструкции `Using` или замените его ресурсом, реализующим <xref:System.IDisposable>.  
  
## См. также  
 <xref:System.IDisposable>   
 [Оператор Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Практическое руководство. Удаление системного ресурса](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)