---
title: "В операторе Next указано больше переменных, чем в соответствующих операторах For | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В операторе Next указано больше переменных, чем в соответствующих операторах For
Вложенные циклы завершены с помощью одного оператора `Next`, в котором задано количество переменных, превышающее количество циклов, как показано в следующем примере:  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **Идентификатор ошибки:** BC32037  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что в операторе `Next` указаны все переменные вложенных циклов в порядке, обратном порядку создания циклов.  
  
2.  Удалите все посторонние переменные из оператора `Next`.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)