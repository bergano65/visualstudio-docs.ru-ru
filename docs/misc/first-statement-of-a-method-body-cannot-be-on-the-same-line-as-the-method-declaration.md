---
title: "Первый оператор тела метода не может находиться в одной строке с объявлением этого метода | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Первый оператор тела метода не может находиться в одной строке с объявлением этого метода
Оператор `Function`, `Sub`, `Get`, `Set` или `Property` должен быть один в строке исходного кода.  
  
 **Идентификатор ошибки:** BC30040  
  
### Исправление ошибки  
  
1.  Удалите метку строки, предшествующую объявлению процедуры.  
  
2.  Переместите все операторы, предшествующие объявлению процедуры, в предыдущую строку исходного кода.  
  
3.  Переместите все операторы, следующие за объявлением процедуры, в следующую строку исходного кода.  
  
## См. также  
 [Процедуры](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [Практическое руководство. Операторы меток](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)