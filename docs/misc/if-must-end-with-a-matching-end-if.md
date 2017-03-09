---
title: "Блок If должен заканчиваться соответствующим оператором End If | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок If должен заканчиваться соответствующим оператором End If
Оператор `If` не имеет соответствующего оператора `End If`. Оператор `End If` должен использоваться для завершения блока `If`.  
  
 **Идентификатор ошибки:** BC30081  
  
### Исправление ошибки  
  
1.  Если этот блок `If` является частью набора вложенных блоков `If`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Добавьте оператор `End If` в конец блока `If`.  
  
## См. также  
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)