---
title: "Exit Do может использоваться только в теле оператора Do | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit Do может использоваться только в теле оператора Do
Оператор `Exit Do` находится за пределами цикла `Do`. Оператор `Exit Do` допустим только между оператором `Do` и соответствующим оператором `Loop`.  
  
 **Идентификатор ошибки:** BC30089  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что допустимый оператор `Do` предшествует оператору `Exit Do` и допустимый оператор `Loop` указан после него.  
  
2.  Убедитесь в том, что другие управляющие структуры в цикле `Do` завершены правильно.  
  
## См. также  
 [Оператор Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)