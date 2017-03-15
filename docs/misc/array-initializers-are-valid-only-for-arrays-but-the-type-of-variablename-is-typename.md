---
title: "Инициализаторы массивов допустимы только для массивов, а &quot;&lt;имя_переменной&gt;&quot; имеет тип &quot;&lt;имя_типа&gt;&quot; | Microsoft Docs"
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
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Инициализаторы массивов допустимы только для массивов, а &quot;&lt;имя_переменной&gt;&quot; имеет тип &quot;&lt;имя_типа&gt;&quot;
Предпринята попытка инициализации переменной, не являющейся массивом, с помощью списка значений.  
  
 **Идентификатор ошибки:** BC30679  
  
### Исправление ошибки  
  
-   Объявите и инициализируйте переменную как массив, например:  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   Инициализируйте переменную как имеющую единственное значение, например:  
  
     `Dim intvalue As Integer = 1`  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Объявление переменной](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)