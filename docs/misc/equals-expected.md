---
title: "Требуется &quot;Equals&quot; | Microsoft Docs"
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
  - "vbc36619"
  - "bc36619"
helpviewer_keywords: 
  - "BC36619"
ms.assetid: 1fd8c0dc-0e87-47b7-ab30-498809cca033
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется &quot;Equals&quot;
Предложение `Join` или `Group Join` было указано без оператора `Equals`. Оператор `Equals` используется для идентификации операции `Boolean` для проверки ключевых полей для сопоставления элементов.  
  
 **Идентификатор ошибки:** BC36619  
  
### Исправление ошибки  
  
1.  Добавьте оператор `Equals` и ключевые поля в предложение `Join` или `Group Join`. Пример:  
  
    ```vb#  
    Dim petOwnersGrouped = From pers In people _ Group Join pet In pets _ On pers Equals pet.Owner _ Into PetList = Group _ Select pers.FirstName, pers.LastName, _ PetList  
    ```  
  
## См. также  
 [Практическое руководство. Объединение данных с помощью соединений](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Предложение Join](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)