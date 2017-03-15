---
title: "Для нескольких переменных, объявленных с одним спецификатором типа, явная инициализация не разрешена | Microsoft Docs"
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
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Для нескольких переменных, объявленных с одним спецификатором типа, явная инициализация не разрешена
Инициализация не разрешена, если одной строке объявляется несколько переменных.  
  
 **Идентификатор ошибки**: BC30671  
  
### Исправление ошибки  
  
1.  Объявите и инициализируйте каждый элемент отдельно.  
  
2.  Объявите несколько элементов вместе, а затем инициализируйте каждый элемент; например:  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)