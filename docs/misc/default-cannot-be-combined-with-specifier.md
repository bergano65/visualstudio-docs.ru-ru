---
title: "Default не может использоваться вместе с &quot;&lt;спецификатор&gt;&quot; | Microsoft Docs"
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
  - "vbc30490"
  - "bc30490"
helpviewer_keywords: 
  - "BC30490"
ms.assetid: fb29622c-a176-4185-94ae-2c1ca85adddb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default не может использоваться вместе с &quot;&lt;спецификатор&gt;&quot;
Предпринята попытка сочетания ключевого слова `Default` со спецификатором, таким как `Shared` или `Private`, который не является допустимым в этом контексте.  
  
 **Идентификатор ошибки:** BC30490  
  
### Исправление ошибки  
  
-   Удалите `Default`.  
  
     \-или\-  
  
-   Удалите конфликтующий спецификатор.  
  
## См. также  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)