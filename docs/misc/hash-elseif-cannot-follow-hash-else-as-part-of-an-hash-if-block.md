---
title: "#ElseIf не может следовать за #Else в пределах блока #If. | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #ElseIf не может следовать за #Else в пределах блока #If.
Директива условной компиляции `#ElseIf` следует за директивой `#Else`. Директива `#Else` должна быть последней директивой в блоке условной компиляции перед директивой `#End If`.  
  
 **Идентификатор ошибки:** BC32030  
  
### Исправление ошибки  
  
1.  Проверьте должна ли перед директивой `#Else` быть директива `#ElseIf`.  
  
2.  Убедитесь, что предыдущий блок `#If` завершается должным образом, и что инициируется новый блок `#If`.  
  
3.  Если все остальное правильно, переместите директиву `#ElseIf` и ее соответствующий блок операторов перед блоком `#Else`.  
  
## См. также  
 [Директивы \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)