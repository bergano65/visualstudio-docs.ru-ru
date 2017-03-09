---
title: "Default может указываться только для одного имени свойства в &lt;тип&gt; | Microsoft Docs"
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
  - "bc30359"
  - "vbc30359"
helpviewer_keywords: 
  - "BC30359"
ms.assetid: d8dd0aa6-ebe1-4601-beec-130edc12f81e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default может указываться только для одного имени свойства в &lt;тип&gt;
Предпринята попытка применить `Default` к нескольким именам свойств в классе, интерфейсе или структуре.  
  
 **Идентификатор ошибки:** BC30359  
  
### Исправление ошибки  
  
-   Удалите все объявления `Default`, кроме одного.  
  
## См. также  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)