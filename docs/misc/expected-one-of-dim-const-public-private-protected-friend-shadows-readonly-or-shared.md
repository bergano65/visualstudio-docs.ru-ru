---
title: "Требуется один из следующих операторов: &quot;Dim&quot;, &quot;Const&quot;, &quot;Public&quot;, &quot;Private&quot;, &quot;Protected&quot;, &quot;Friend&quot;, &quot;Shadows&quot;, &quot;ReadOnly&quot; или &quot;Shared&quot; | Microsoft Docs"
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
  - "bc30195"
  - "vbc30195"
helpviewer_keywords: 
  - "BC30195"
ms.assetid: 95684eaa-5aa2-4ae4-9a73-5f97c491e02c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется один из следующих операторов: &quot;Dim&quot;, &quot;Const&quot;, &quot;Public&quot;, &quot;Private&quot;, &quot;Protected&quot;, &quot;Friend&quot;, &quot;Shadows&quot;, &quot;ReadOnly&quot; или &quot;Shared&quot;
В операторе объявления отсутствует ключевое слово объявления. Одна из возможных причин заключается в том, что объявление атрибута вызывает метод.  
  
 **Идентификатор ошибки:** BC30195  
  
### Исправление ошибки  
  
1.  Проверьте, объявлен ли метод в рамках объявления атрибута.  
  
2.  Укажите в начале оператора соответствующее ключевое слово объявления.  
  
## См. также  
 [Объявленные элементы](/dotnet/visual-basic/programming-guide/language-features/declared-elements/index)   
 [Массивы не могут объявляться с помощью ключевого слова "New".](../misc/arrays-cannot-be-declared-with-new.md)