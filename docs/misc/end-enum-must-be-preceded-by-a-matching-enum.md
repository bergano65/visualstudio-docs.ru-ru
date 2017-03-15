---
title: "Оператору &quot;End Enum&quot; должен предшествовать соответствующий оператор &quot;Enum&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30184"
  - "vbc30184"
helpviewer_keywords: 
  - "BC30184"
ms.assetid: b7f5ebf0-10c8-4320-8caf-dffc24ae8a71
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;End Enum&quot; должен предшествовать соответствующий оператор &quot;Enum&quot;.
Оператор `End Enum` не имеет соответствующего оператора `Enum`. Оператору `End Enum` должен предшествовать соответствующий оператор `Enum`.  
  
 **Идентификатор ошибки:** BC30184  
  
### Исправление ошибки  
  
1.  Убедитесь, что предшествующий оператор `Enum` указан без ошибок и является допустимым.  
  
2.  Проверьте правильность формата членов `Enum`.  
  
## См. также  
 [Оператор Enum](/dotnet/visual-basic/language-reference/statements/enum-statement)