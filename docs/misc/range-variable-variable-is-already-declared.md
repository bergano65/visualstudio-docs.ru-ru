---
title: "Переменная диапазона &lt;переменная&gt; уже объявлена | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36600"
  - "bc36600"
helpviewer_keywords: 
  - "BC36600"
ms.assetid: d53da04d-cd36-44ec-8b23-48cd81231191
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная диапазона &lt;переменная&gt; уже объявлена
Имя переменной диапазона, указанное в предложении `Select` или в части `Into` предложения `Aggregate`, `Group By` или `Group Join`, дублирует имя переменной диапазона, которая уже указана в предложении запроса.  
  
 **Идентификатор ошибки:** BC36600  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что все переменные диапазона в предложении запроса имеют уникальные имена.  
  
## См. также  
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Предложение Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Предложение Select](/dotnet/visual-basic/language-reference/queries/select-clause)   
 [Предложение Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)