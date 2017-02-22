---
title: "Задача FormatUrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "FormatUrl - задача [MSBuild]"
  - "MSBuild, FormatUrl - задача"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача FormatUrl
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Преобразование URL\-адреса в правильный формат URL\-адреса.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `FormatUrl`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`InputUrl`|Необязательный параметр типа `String`.<br /><br /> Указывает URL\-адрес для форматирования.|  
|`OutputUrl`|Необязательный выходной параметр типа `String`.<br /><br /> Указывает отформатированный URL\-адрес.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)