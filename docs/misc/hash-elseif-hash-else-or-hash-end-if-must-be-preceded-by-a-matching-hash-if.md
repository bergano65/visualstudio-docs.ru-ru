---
title: "Директиве &quot;#ElseIf&quot;, &quot;#Else&quot; или &quot;#End If&quot; должна предшествовать соответствующая директива &quot;#If&quot;. | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Директиве &quot;#ElseIf&quot;, &quot;#Else&quot; или &quot;#End If&quot; должна предшествовать соответствующая директива &quot;#If&quot;.
`#ElseIf`, `#Else` и `#End If` являются директивами условной компиляции. Перед директивой `#ElseIf`, `#Else` или `#End If` не указана соответствующая директива `#If`.  
  
 **Идентификатор ошибки:** BC30013  
  
### Исправление ошибки  
  
1.  Убедитесь, что предполагаемая директива `#If` не отделена от соответствующего предложения промежуточным блоком условной компиляции или неправильно размещенной директивой `#End If`.  
  
    > [!NOTE]
    >  В каждом блоке `#If` разрешена только одна директива `#Else`, поэтому две последовательных директивы `#Else` вызывают эту ошибку.  
  
2.  Убедитесь, что начальный символ `#` не пропущен в предыдущей директиве `#If`.  
  
3.  Если все остальное в порядке, добавьте директиву `#If` в начало блока условной компиляции.  
  
## См. также  
 [Директивы \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)