---
title: "Переменная диапазона &quot;&lt;переменная&gt;&quot; скрывает переменную во внешнем блоке или переменную диапазона, ранее определенную в выражении запроса. | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная диапазона &quot;&lt;переменная&gt;&quot; скрывает переменную во внешнем блоке или переменную диапазона, ранее определенную в выражении запроса.
Переменная диапазона в запросе имеет то же имя, что и ранее определенная в той же области переменная или ранее определенная в запросе переменная диапазона.  
  
 **Идентификатор ошибки:** BC30978  
  
### Исправление ошибки  
  
-   Убедитесь в том, что все переменные диапазонов в запросе имеют уникальные имена, которые не дублируют существующие имена переменных в той же области.  
  
-   Заключите вложенные запросы с повторяющимися именами управляющих переменных в круглые скобки, разделив области каждой переменной диапазона.  
  
## См. также  
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)