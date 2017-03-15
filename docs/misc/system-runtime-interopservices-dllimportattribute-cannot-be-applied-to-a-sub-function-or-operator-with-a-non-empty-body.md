---
title: "System.Runtime.InteropServices.DllImportAttribute не может использоваться для Sub, Function или Operator с непустым телом. | Microsoft Docs"
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
  - "bc31522"
  - "vbc31522"
helpviewer_keywords: 
  - "BC31522"
ms.assetid: 9548cf98-8a13-4f09-b6b5-2f57273c1571
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute не может использоваться для Sub, Function или Operator с непустым телом.
Атрибут `DllImportAttribute` применен к процедуре `Sub``Function` или `Operator`, которая не является пустой.  
  
 **Идентификатор ошибки:** BC31522  
  
### Исправление ошибки  
  
-   Удалите весь код из `Sub`, `Function` или `Operator`, чтобы использовать этот атрибут.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)