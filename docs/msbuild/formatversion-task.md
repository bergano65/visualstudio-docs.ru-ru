---
title: "Задача FormatVersion | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача FormatVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Добавляет номер редакции к номеру версии.  
  
-   Case \#1: Input: Version\=\<не\_определено\>; Revision\=\<неважно\>; Output: OutputVersion\="1.0.0.0"  
  
-   Case \#2: Input: Version\="1.0.0.\*" Revision\="5" Output: OutputVersion\="1.0.0.5"  
  
-   Case \#3: Input: Version\="1.0.0.0" Revision\=\<don't care\>; Output: OutputVersion\="1.0.0.0"  
  
## Параметры  
 В следующей таблице описаны параметры задачи `FormatVersion`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`FormatType`|Необязательный параметр типа `String`.<br /><br /> Указывает тип формата.<br /><br /> -   "Version" \= version.<br />-   "Path" \= replace "." with "\_";|  
|`OutputVersion`|Необязательный выходной параметр типа `String`.<br /><br /> Задает Выходная версию, содержащая номера редакции.|  
|`Revision`|Необязательный параметр типа `Int32`.<br /><br /> Задает редакцию, которую следует добавить к версии.|  
|`Version`|Необязательный параметр типа `String`.<br /><br /> Указывает строку номера версии для форматирования.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)