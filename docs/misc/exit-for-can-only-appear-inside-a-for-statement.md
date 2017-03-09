---
title: "Exit For может использоваться только в теле оператора For | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit For может использоваться только в теле оператора For
Оператор `Exit For` находится за пределами цикла `For`. Оператор `Exit For` допустим только между оператором `For` или `For Each` и соответствующим оператором `Next`.  
  
 **Идентификатор ошибки:** BC30096  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что допустимый оператор `For` или `For Each` предшествует оператору `Exit For` и допустимый оператор `Next` указан после него.  
  
2.  Убедитесь в том, что другие управляющие структуры в цикле `For` завершены правильно.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Оператор For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)