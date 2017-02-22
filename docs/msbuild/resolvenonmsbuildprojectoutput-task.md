---
title: "Задача ResolveNonMSBuildProjectOutput | Microsoft Docs"
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
  - "MSBuild, ResolveNonMSBuildProjectOutput - задача"
  - "ResolveNonMSBuildProjectOutput - задача [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача ResolveNonMSBuildProjectOutput
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определение выходных файлов для ссылок на проекты, не относящиеся к MSBuild.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `ResolveNonMSBuildProjectOutput`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`PreresolvedProjectOutputs`|Необязательный параметр типа `String`.<br /><br /> Задает XML\-строку, содержащую разрешенные выходные файлы проекта.|  
|`ProjectReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает ссылки на проект.|  
|`ResolvedOutputPaths`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит список разрешенных путей ссылок с сохранением исходных атрибутов ссылок на проекты.|  
|`UnresolvedProjectReferences`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит список элементов ссылок на проекты, которые нельзя разрешить с помощью предварительно разрешенного списка выходных файлов.<br /><br /> Поскольку Visual Studio только предварительно разрешает проекты, не относящиеся к MSBuild, ссылки на проекты в этом списке представлены в формате MSBuild.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)