---
title: "Оператору End Using должен предшествовать соответствующий ему оператор Using | Microsoft Docs"
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
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору End Using должен предшествовать соответствующий ему оператор Using
Оператору `End Using` не предшествует соответствующее объявление `Using`.  
  
 **Идентификатор ошибки:** BC36007  
  
### Исправление ошибки  
  
-   Удалите оператор `End Using`, если он лишний.  
  
-   Добавьте объявление [Оператор Using](/dotnet/visual-basic/language-reference/statements/using-statement), если оно отсутствует.  
  
-   Переместите оператор `End Using` в соответствующее место кода.  
  
## См. также  
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)