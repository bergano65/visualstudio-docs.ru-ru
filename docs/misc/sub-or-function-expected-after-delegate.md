---
title: "После Delegate требуется Sub или Function. | Microsoft Docs"
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
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# После Delegate требуется Sub или Function.
Оператор `Delegate` не указывает процедуру `Sub` или `Function`. Ключевое слово `Sub` или `Function` должно следовать сразу за ключевым словом `Delegate`.  
  
 **Идентификатор ошибки:** BC30278  
  
### Исправление ошибки  
  
1.  Добавьте ключевое слово `Sub` или `Function` сразу после `Delegate`.  
  
2.  Укажите имя процедуры, список аргументов и тип возврата.  
  
## См. также  
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Процедуры](/dotnet/visual-basic/programming-guide/language-features/procedures/index)