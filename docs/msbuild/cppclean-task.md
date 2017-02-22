---
title: "Задача CPPClean | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "CPPClean - задача (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), CPPClean - задача"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача CPPClean
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Удаляет временные файлы, которые MSBuild создает при построении проекта Visual C\+\+.  Процесс удаления файлов построения называется *очисткой*.  
  
## Параметры  
 В следующей таблице описаны параметры задачи **CPPClean** .  
  
|Параметр|Описание|  
|--------------|--------------|  
|**DeletedFiles**|Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**DoDelete**|Необязательный параметр типа **Boolean**.<br /><br /> Если он имеет значение `true`, выполняется очистка временных файлов построения.|  
|**FilePatternsToDeleteOnClean**|Обязательный параметр типа `String`.<br /><br /> Задает разделенный точками с запятой список расширений файлов, предназначенных для очистки.|  
|**FilesExcludedFromClean**|Необязательный параметр типа `String`.<br /><br /> Задает список разделенных точками с запятой файлов, которые не следует очищать.|  
|**FoldersToClean**|Обязательный параметр типа `String`.<br /><br /> Задает список разделенных точками с запятой каталогов для очистки.  Можно указать полный или относительный путь, а путь может содержать подстановочный символ \(**\***\).|  
  
## Заметки  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)