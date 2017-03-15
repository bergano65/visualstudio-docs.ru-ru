---
title: "Exit While может использоваться только в теле оператора While | Microsoft Docs"
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
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit While может использоваться только в теле оператора While
Оператор `Exit While` находится за пределами блока `While`. Оператор `Exit While` допустим только между оператором `While` и соответствующим оператором `End While`.  
  
 **Идентификатор ошибки:** BC30097  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что допустимый оператор `While` предшествует оператору `Exit While` и допустимый оператор `End While` указан после него.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `While` завершаются правильно.  
  
## См. также  
 [Оператор While...End While](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)