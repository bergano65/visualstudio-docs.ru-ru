---
title: "Явная инициализация массивов, объявленных с явными границами, запрещена. | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Явная инициализация массивов, объявленных с явными границами, запрещена.
Не удается инициализировать массивы, если они объявлены с определенным размером.  
  
 **Идентификатор ошибки**: BC30672  
  
### Исправление ошибки  
  
-   Объявите массив, а затем инициализируйте его отдельно.  
  
-   Объявите и инициализируйте массив как динамический и при необходимости используйте `ReDim`, например:  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## См. также  
 [Массивы](/dotnet/visual-basic/programming-guide/language-features/arrays/index)