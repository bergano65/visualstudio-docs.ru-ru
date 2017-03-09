---
title: "Символ типа не может использоваться в объявлении Sub, так как Sub не возвращает значение. | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Символ типа не может использоваться в объявлении Sub, так как Sub не возвращает значение.
Процедура `Sub`, например `Function`, является отдельной процедурой, которая может принимать аргументы и выполнять последовательность операторов. В отличие от процедуры `Function`, `Sub` не возвращает значение и, следовательно, не может содержать объявление типа.  
  
 **Идентификатор ошибки:** BC30303  
  
### Исправление ошибки  
  
-   Измените процедуру `Sub` на процедуру `Function`.  
  
## См. также  
 [Подпрограммы](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)