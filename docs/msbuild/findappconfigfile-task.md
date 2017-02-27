---
title: "Задача FindAppConfigFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "FindAppConfigFile - задача [MSBuild]"
  - "MSBuild, FindAppConfigFile - задача"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Задача FindAppConfigFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Находит файл app.config, если он имеется, в предоставленных списках.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `FindAppConfigFile`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AppConfigFile`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает первый совпадающий элемент в списке, если таковой имеется.|  
|`PrimaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает Основной список, в котором следует выполнить поиск.|  
|`SecondaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает Дополнительный список, в котором следует выполнить поиск.|  
|`TargetPath`|Обязательный параметр типа `String`.<br /><br /> Указывает значение для добавления в качестве метаданных.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)