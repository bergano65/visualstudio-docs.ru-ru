---
title: "Метки за пределами методов/многострочных лямбда-выражений недействительны | Microsoft Docs"
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
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метки за пределами методов/многострочных лямбда-выражений недействительны
Вы можете добавлять метку в оператор только в `Sub`, `Function`, свойстве `Get` или свойстве `Set` процедуры. Только исполняемый оператор может иметь метку, и все исполняемые операторы должны находиться внутри процедур.  
  
 **Идентификатор ошибки:** BC30016  
  
### Исправление ошибки  
  
1.  Удалите метку из оператора или переместите оператор в процедуру.  
  
## См. также  
 [Практическое руководство. Операторы меток](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Оператор Sub](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement)