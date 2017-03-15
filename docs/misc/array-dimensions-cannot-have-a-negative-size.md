---
title: "Размерности массива не могут быть отрицательными | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30611"
  - "vbc30611"
helpviewer_keywords: 
  - "BC30611"
ms.assetid: e310bd0d-f221-4b02-87f3-02124f4de87c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Размерности массива не могут быть отрицательными
При задании одной или нескольких границ массива использовано отрицательное значение. Нижний индекс может быть отрицательным только в том случае, если значение верхней границы равно –1; в этом случае объявляется пустой массив. Такой массив не содержит элементов, но он не эквивалентен `Nothing`.  
  
 **Идентификатор ошибки:** BC30611  
  
### Исправление ошибки  
  
-   Укажите положительное значение границы массива вместо отрицательного.  
  
## См. также  
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)