---
title: "System.Runtime.InteropServices.DllImportAttribute не может применяться к Get или Set | Microsoft Docs"
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
  - "vbc31524"
  - "bc31524"
helpviewer_keywords: 
  - "BC31524"
ms.assetid: 3603e33a-a80b-448d-83e0-e5dbc9af4dcf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute не может применяться к Get или Set
Атрибут `DllImportAttribute` применен к процедуре свойства `Get` или `Set`.  
  
 **Идентификатор ошибки:** BC31524  
  
### Исправление ошибки  
  
1.  Удалите атрибут `DllImportAttribute` из процедур свойства `Get` и `Set`.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)