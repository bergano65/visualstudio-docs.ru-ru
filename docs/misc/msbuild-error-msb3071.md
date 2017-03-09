---
title: "Ошибка MSBuild MSB3071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3071
**Использованы все буквы дисков от A: to Z:.  Так как рабочий каталог "\<путь\>" является UNC\-путем, задаче "Exec" требуется свободная буква диска, чтобы сопоставить с ней UNC\-путь.  Отключитесь от одного или нескольких общих ресурсов, чтобы освободить буквы дисков или укажите локальный рабочий каталог перед повтором этой команды.**  
  
 Все буквы дисков от A: до Z: в настоящее время используются.  Поскольку указанный рабочий каталог представляет собой UNC\-путь, задаче `Exec` требуется свободная буква диска, чтобы назначить UNC\-пути.  
  
### Чтобы исправить эту ошибку  
  
-   Отключитесь от одного или нескольких общих ресурсов, чтобы освободить буквы дисков.  
  
-   Перед повторной попыткой выполнения команды укажите локальный рабочий каталог.  
  
## См. также  
 [Задача Exec](../msbuild/exec-task.md)