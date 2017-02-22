---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Сравнение двух файлов.  Различия отображаются в специальном окне Visual Studio.  
  
## Синтаксис  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## Аргументы  
 `SourceFile`  
 Обязательное.  Полный путь и имя первого файла, с которым выполняется сравнение.  
  
 `TargetFile`  
 Обязательное.  Полный путь и имя второго файла, с которым будет сравниваться  
  
 `SourceDisplayName`  
 Необязательный параметр.  Отображаемое имя первого файла.  
  
 `TargetDisplayName`  
 Необязательный параметр.  Отображаемое имя второго файла.