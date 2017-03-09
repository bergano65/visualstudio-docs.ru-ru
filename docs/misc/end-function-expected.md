---
title: "Требуется End Function | Microsoft Docs"
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
  - "vbc30027"
  - "bc30027"
helpviewer_keywords: 
  - "BC30027"
ms.assetid: 5ee1a8ae-d0cb-437d-966e-aba0ea4d3106
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется End Function
Оператор `End` должен соответствовать блоку, который он завершает. Определение процедуры`Function` не завершается должным образом.  
  
 **Идентификатор ошибки:** BC30027  
  
### Исправление ошибки  
  
-   Добавьте оператор `End Function` в конец процедуры.  
  
## См. также  
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Оператор End](/dotnet/visual-basic/language-reference/statements/end-statement)