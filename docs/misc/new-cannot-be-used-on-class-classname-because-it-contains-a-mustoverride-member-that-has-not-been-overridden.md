---
title: "New не может использоваться в классе &quot;&lt;имя_класса&gt;&quot;, так как он содержит член со спецификатором MustOverride, который не был переопределен | Microsoft Docs"
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
  - "bc30376"
  - "vbc30376"
helpviewer_keywords: 
  - "BC30376"
ms.assetid: f3aed05a-8202-4d2d-9c49-3c000d055116
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# New не может использоваться в классе &quot;&lt;имя_класса&gt;&quot;, так как он содержит член со спецификатором MustOverride, который не был переопределен
Предпринята попытка использования `New` в классе, содержащем член `MustOverride`, который не был переопределен.  
  
 **Идентификатор ошибки:** BC30376  
  
### Исправление ошибки  
  
-   Удалите оператор `New`.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)