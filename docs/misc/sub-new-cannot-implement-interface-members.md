---
title: "Sub New не может реализовывать члены интерфейса | Microsoft Docs"
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
  - "bc31042"
  - "vbc31042"
helpviewer_keywords: 
  - "BC31042"
ms.assetid: 43ad231f-878d-4d08-b43c-06bf167ddd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub New не может реализовывать члены интерфейса
`Sub New` представляет собой конструктор и не может реализовывать члены.  
  
 **Идентификатор ошибки:** BC31042  
  
### Исправление ошибки  
  
-   Удалите операторы `Implements` из процедур `Sub New`.  
  
## См. также  
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)