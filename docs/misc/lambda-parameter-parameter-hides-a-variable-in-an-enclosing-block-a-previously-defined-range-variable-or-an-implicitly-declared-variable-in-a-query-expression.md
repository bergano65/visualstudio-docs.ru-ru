---
title: "Лямбда-параметр &quot;&lt;параметр&gt;&quot; скрывает переменную во внешнем блоке, ранее определенную переменную диапазона или неявно объявленную переменную в выражении запроса. | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Лямбда-параметр &quot;&lt;параметр&gt;&quot; скрывает переменную во внешнем блоке, ранее определенную переменную диапазона или неявно объявленную переменную в выражении запроса.
Переменная в лямбда\-выражении имеет то же имя, что и переменная, определенная ранее в той же области. Это может быть переменная во внешнем блоке кода для вложенного лямбда\-выражения, переменная диапазона, ранее определенная в запросе LINQ, или переменная, неявно объявленная для запроса LINQ.  
  
 **Идентификатор ошибки:** BC36641  
  
### Исправление ошибки  
  
-   Убедитесь, что все переменные в лямбда\-выражении имеют уникальные имена, которые не дублируют существующие имена переменных в той же области.  
  
## См. также  
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)