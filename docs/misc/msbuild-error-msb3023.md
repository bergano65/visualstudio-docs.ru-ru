---
title: "Ошибка MSBuild MSB3023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3023
**Не указана папка назначения для задачи Copy.  Укажите "\<атрибут\>" или "\<атрибут\>".**  
  
 Назначение для задачи `Copy` необходимо указать с помощью одного из атрибутов `DestinationFiles`и`DestinationDirectory`.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите `DestinationFiles`или`DestinationDirectory`для задачи `Copy`.  
  
## См. также  
 [Задача Copy](../msbuild/copy-task.md)   
 [Задачи](../msbuild/msbuild-tasks.md)