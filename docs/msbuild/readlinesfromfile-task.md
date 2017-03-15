---
title: "Задача ReadLinesFromFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ReadLinesFromFile - задача"
  - "ReadLinesFromFile - задача [MSBuild]"
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Задача ReadLinesFromFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Чтение списка элементов из текстового файла.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `ReadLinesFromFile`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Этот параметр указывает считываемый файл.  В каждой строке файла должен содержаться один элемент.|  
|`Lines`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Этот параметр содержит строки, считываемые из файла.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `ReadLinesFromFile` используется для создания элементов из списка в текстовом файле.  Элементы, считываемые из этого файла, сохраняются в коллекции элементов `ItemsFromFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
    </ItemGroup>  
  
    <Target Name="ReadFromFile">  
        <ReadLinesFromFile  
            File="@(MyTextFile)" >  
            <Output  
                TaskParameter="Lines"  
                ItemName="ItemsFromFile"/>  
        </ReadLinesFromFile>  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)   
 [Задачи](../msbuild/msbuild-tasks.md)