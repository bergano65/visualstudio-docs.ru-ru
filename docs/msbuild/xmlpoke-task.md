---
title: "Задача XmlPoke | Microsoft Docs"
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
  - "MSBuild, XmlPoke - задача"
  - "XmlPoke - задача [MSBuild]"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Задача XmlPoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Устанавливает в XML\-файле значения, указанные в запросе XPath.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `XmlPoke`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Namespaces`|Необязательный параметр типа `String`.<br /><br /> Задает пространства имен для префиксов запросов XPath.|  
|`Query`|Необязательный параметр типа `String`.<br /><br /> Указывает запрос XPath.|  
|`Value`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает выходной файл.|  
|`XmlInputPath`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает входные XML\-данные в качестве пути к файлу.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)