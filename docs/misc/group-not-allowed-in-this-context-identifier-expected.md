---
title: "В данном контексте ключевое слово Group не разрешено; требуется идентификатор | Microsoft Docs"
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
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В данном контексте ключевое слово Group не разрешено; требуется идентификатор
Ключевое слово `Group` включено в раздел `Into` предложения `Aggregate`. Ключевое слово `Group` допустимо только в предложениях `Group By` или `Group Join`.  
  
 **Идентификатор ошибки:** BC36618  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Group` из предложения `Aggregate`. Вы можете добавить предложение `Group By` в запрос для группирования результатов.  
  
## См. также  
 [Предложение Aggregate](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Предложение Group By](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Предложение Group Join](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)