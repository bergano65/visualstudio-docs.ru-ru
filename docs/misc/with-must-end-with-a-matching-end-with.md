---
title: "Блок With должен заканчиваться соответствующим оператором End With. | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок With должен заканчиваться соответствующим оператором End With.
Оператор `With` не имеет соответствующего оператора `End With`. Оператор `End With` должен использоваться для завершения блока `With`.  
  
 **Идентификатор ошибки:** BC30085  
  
### Исправление ошибки  
  
-   Если этот блок `With` является частью набора вложенных блоков `With`, убедитесь в том, что каждый блок завершается правильно.  
  
-   Добавьте оператор `End With` в конец блока `With`.  
  
## См. также  
 [Оператор With...End With](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)