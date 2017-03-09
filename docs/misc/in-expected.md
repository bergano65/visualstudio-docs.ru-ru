---
title: "Требуется In | Microsoft Docs"
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
  - "bc36607"
  - "vbc36607"
helpviewer_keywords: 
  - "BC36607"
ms.assetid: f390bca5-12fe-4fe1-bd86-7f8ab66dfbd8
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется In
Предложение `From` или `Aggregate` было указано без оператора `In`. Вы используете оператор `In` для идентификации коллекции для запроса.  
  
 **Идентификатор ошибки:** BC36607  
  
### Исправление ошибки  
  
1.  Добавьте оператор `In` и ключевые поля в предложение `From` или `Aggregate`. Ниже представлен пример такого кода.  
  
    ```vb#  
    Dim names = From pers In people Select pers.FirstName, pers.LastName  
    ```  
  
## См. также  
 [Предложение From](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Предложение Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)