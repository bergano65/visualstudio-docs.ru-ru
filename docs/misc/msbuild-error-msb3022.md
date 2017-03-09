---
title: "Ошибка MSBuild MSB3022 | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3022
**В файле проекта в качестве входных параметров указаны "\<атрибут\>" и "\<атрибут\>".  Выберите один из них.**  
  
 Для задачи `Copy` необходимо указать либо `DestinationFiles`, либо `DestinationDirectory`, но не оба атрибута задачи одновременно.  
  
### Чтобы исправить эту ошибку  
  
-   В файле проекта укажите для задачи `Copy` атрибут `DestinationFiles` или `DestinationDirectory`.  
  
## См. также  
 [Задача Copy](../msbuild/copy-task.md)   
 [Задачи](../msbuild/msbuild-tasks.md)