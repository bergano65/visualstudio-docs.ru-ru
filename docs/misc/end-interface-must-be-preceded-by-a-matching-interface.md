---
title: "Оператору &quot;End Interface&quot; должен предшествовать соответствующий оператор &quot;Interface&quot;. | Microsoft Docs"
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
  - "vbc30252"
  - "bc30252"
helpviewer_keywords: 
  - "BC30252"
ms.assetid: 1a2c3278-5dd7-4a72-9dca-3f2a5bdfd04c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;End Interface&quot; должен предшествовать соответствующий оператор &quot;Interface&quot;.
Оператор `End Interface` не имеет соответствующего оператора `Interface`. Оператору `End Interface` должен предшествовать соответствующий оператор `Interface`.  
  
 **Идентификатор ошибки:** BC30252  
  
### Исправление ошибки  
  
1.  Проверьте, не указан ли предшествующий оператор `Interface` с ошибками, и является ли он допустимым.  
  
2.  Проверьте правильность формата членов `Interface`.  
  
## См. также  
 [Оператор Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)