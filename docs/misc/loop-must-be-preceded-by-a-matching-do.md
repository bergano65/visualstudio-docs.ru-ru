---
title: "Оператору &quot;Loop&quot; должен предшествовать соответствующий оператор &quot;Do&quot; | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;Loop&quot; должен предшествовать соответствующий оператор &quot;Do&quot;
Оператор `Loop` не имеет соответствующего оператора `Do`. Оператору `Loop` должен предшествовать соответствующий оператор `Do`.  
  
 **Идентификатор ошибки:** BC30091  
  
### Исправление ошибки  
  
1.  Если этот цикл `Do` является частью набора вложенных циклов `Do`, убедитесь, что каждый цикл завершен правильно.  
  
2.  Убедитесь, что управляющие структуры в цикле `Do` завершены правильно.  
  
3.  Убедитесь, что цикл `Do` имеет правильный формат.  
  
## См. также  
 [Оператор Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)