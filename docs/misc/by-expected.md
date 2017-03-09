---
title: "Требуется &quot;By&quot; | Microsoft Docs"
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
  - "vbc36605"
  - "bc36605"
helpviewer_keywords: 
  - "BC36605"
ms.assetid: d0397b6e-bfc2-400c-92fc-efe82036cfdb
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется &quot;By&quot;
Предложение `Order By` или `Group By` было указано без ключевого слова `By`.  
  
 **Идентификатор ошибки:** BC36605  
  
### Исправление ошибки  
  
1.  Добавьте ключевое слово `By` в предложение `Order By` или `Group By`. Ниже представлен пример такого кода.  
  
    ```vb#  
    Dim customersByCountry = From cust In customers _  
                             Order By cust.Country, cust.City _  
                             Group By CountryName = cust.Country _  
                             Into RegionalCustomers = Group, Count() _  
                             Order By CountryName  
    ```  
  
## См. также  
 [Практическое руководство. Сортировка результатов запроса](../Topic/How%20to:%20Sort%20Query%20Results%20by%20Using%20LINQ%20\(Visual%20Basic\).md)   
 [Предложение Order By](/dotnet/visual-basic/language-reference/queries/order-by-clause)   
 [Предложение Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)