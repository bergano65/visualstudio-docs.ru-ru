---
title: "Оператор &quot;GoTo &lt;имя_метки&gt;&quot; является недопустимым, так как &quot;&lt;имя_метки&gt;&quot; находится в теле оператора SyncLock, который не содержит этот оператор | Microsoft Docs"
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
  - "bc30755"
  - "vbc30755"
helpviewer_keywords: 
  - "BC30755"
ms.assetid: 95fb48c1-4982-45fc-81f0-f30cf0df173f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;GoTo &lt;имя_метки&gt;&quot; является недопустимым, так как &quot;&lt;имя_метки&gt;&quot; находится в теле оператора SyncLock, который не содержит этот оператор
Нельзя осуществлять ветвление в блок `SyncLock`.  
  
 **Идентификатор ошибки:** BC30755  
  
### Исправление ошибки  
  
-   Перестройте ваш код, чтобы метка располагалась перед блоком `SyncLock`.  
  
## См. также  
 [Оператор SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)