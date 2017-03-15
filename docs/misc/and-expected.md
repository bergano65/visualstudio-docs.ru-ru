---
title: "Требуется And | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется And
Для объединения двух или более операторов `Equals` в предложении `Join` или `Group Join` используется оператор сравнения, отличный от `And`. Только оператор `And` может объединять несколько операторов `Equals` в предложении `Join` или `Group Join`.  
  
 **Идентификатор ошибки:** BC36620  
  
### Исправление ошибки  
  
1.  Реструктурируйте предложения `Equals`, чтобы проводить сравнения только с помощью оператора `And`. Ниже представлен пример такого кода.  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## См. также  
 [Практическое руководство. Объединение данных с помощью соединений](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Предложение Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)