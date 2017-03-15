---
title: "Конструктор должен объявляться как подпрограмма, а не как функция. | Microsoft Docs"
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
  - "bc30493"
  - "vbc30493"
helpviewer_keywords: 
  - "BC30493"
ms.assetid: bcacfd4b-cac0-4ad3-a6df-5fb37c189e8f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Конструктор должен объявляться как подпрограмма, а не как функция.
Предпринята попытка объявления `Function New`. Конструкторы должны быть объявлены как `Sub New`.  
  
 **Идентификатор ошибки:** BC30493  
  
### Исправление ошибки  
  
-   Используйте `Sub` вместо `Function`.  
  
## См. также  
 [Оператор Sub](/dotnet/visual-basic/language-reference/statements/sub-statement)