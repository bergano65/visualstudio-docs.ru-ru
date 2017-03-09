---
title: "Оператору Else должен предшествовать соответствующий оператор If или ElseIf. | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору Else должен предшествовать соответствующий оператор If или ElseIf.
`#Else` является директивой условной компиляции. Директиве `#Else` не предшествует соответствующая директива `#If` или `#ElseIf`.  
  
 **Идентификатор ошибки:** BC30028  
  
### Исправление ошибки  
  
1.  Убедитесь, что предшествующая директива `#If` или `#ElseIf` не отделена от этой директивы `#Else` блоком условной компиляции или неправильно размещенной директивой `#End If`.  
  
2.  Убедитесь, что директиве `#Else` предшествует другая директива `#Else`. Если это так, удалите `#Else` или измените ее на `#ElseIf`.  
  
3.  Если все остальное в порядке, добавьте директиву `#If` в начало блока условной компиляции.  
  
## См. также  
 [Директивы \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)