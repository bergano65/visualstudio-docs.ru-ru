---
title: "Exit Select может использоваться только в теле оператора Select | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit Select может использоваться только в теле оператора Select
Оператор `Exit Select` находится за пределами блока `Select`. Оператор `Exit Select` допустим только между оператором `Select` или `Select Case` и соответствующим оператором `End Select`.  
  
 **Идентификатор ошибки:** BC30099  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что допустимый оператор `Select` или `Select Case` предшествует оператору `Exit Select` и допустимый оператор `End Select` указан после него.  
  
2.  Убедитесь в том, что другие управляющие структуры в блоке `Select` завершаются правильно.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)