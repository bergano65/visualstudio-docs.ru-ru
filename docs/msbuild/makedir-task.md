---
title: "Задача MakeDir | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MakeDir - задача [MSBuild]"
  - "MSBuild, MakeDir - задача"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Задача MakeDir
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создание каталогов и, при необходимости, любых родительских каталогов.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `MakeDir`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Directories`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Набор каталогов, которые требуется создать.|  
|`DirectoriesCreated`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Каталоги, созданные этой задачей.  Если некоторые каталоги создать невозможно, в данном наборе будут содержаться не все элементы, передаваемые параметру `Directories`.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере кода задача `MakeDir` используется для создания каталога, указанного в свойстве `OutputDirectory`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)