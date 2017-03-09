---
title: "System.Runtime.InteropServices.DllImportAttribute не может использоваться для &#39;Declare&#39; | Microsoft Docs"
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
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute не может использоваться для &#39;Declare&#39;
Атрибут `DllImportAttribute` был применен к функции `Declare`. Этот атрибут может использоваться только с пустым оператором `Function` или `Sub`.  
  
 **Идентификатор ошибки:** BC31523  
  
### Исправление ошибки  
  
1.  Удалите атрибут `DllImportAttribute` из оператора `Declare`.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Оператор Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)