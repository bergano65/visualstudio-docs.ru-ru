---
title: "Блок Select Case должен заканчиваться соответствующим оператором End Select | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок Select Case должен заканчиваться соответствующим оператором End Select
Оператор `Select` или `Select Case` не имеет соответствующего оператора `End Select`. Оператор `End Select` должен использоваться для завершения блока `Select`.  
  
 **Идентификатор ошибки:** BC30095  
  
### Исправление ошибки  
  
1.  Если этот блок `Select` является частью набора вложенных блоков `Select`, убедитесь в том, что каждый блок завершается правильно.  
  
2.  Добавьте оператор `End Select` в конец блока `Select`.  
  
## См. также  
 [Оператор Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)