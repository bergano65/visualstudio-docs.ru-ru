---
title: "Ошибка MSBuild MSB3072 | Microsoft Docs"
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
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3072
**Для выполнения задаче "Exec" требуется команда.**  
  
 Атрибут `Command` является обязательным атрибутом для задачи `Exec`.  
  
### Чтобы исправить эту ошибку  
  
1.  В файле проекта укажите для задачи `Exec` атрибут `Command`.  
  
## См. также  
 [Задача Exec](../msbuild/exec-task.md)   
 [Задачи](../msbuild/msbuild-tasks.md)