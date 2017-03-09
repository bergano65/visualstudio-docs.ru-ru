---
title: "Требуется директива If, ElseIf, Else, End If или Const. | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется директива If, ElseIf, Else, End If или Const.
Исходная строка начинается с символа `#`, но допустимая директива условной компиляции не указана сразу за `#`. К допустимым директивам относятся `#Const`, `#ExternalSource`, `#If`, `#Else`, `#ElseIf`, `#End If` и `#Region`.  
  
 **Идентификатор ошибки:** BC30248  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания директивы условной компиляции.  
  
2.  Убедитесь, что нет промежуточных пробелов между символом `#` и директивой.  
  
3.  Удалите символ `#` или добавьте допустимую директиву непосредственно после него.  
  
## См. также  
 [Директивы](/dotnet/visual-basic/language-reference/directives/directives)