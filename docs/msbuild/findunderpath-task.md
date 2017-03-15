---
title: "Задача FindUnderPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "FindUnderPath - задача [MSBuild]"
  - "MSBuild, FindUnderPath - задача"
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Задача FindUnderPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет, какие элементы в указанном наборе имеют пути в указанной папке или на более низком уровне.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `FindUnderPath`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает файлы, пути которых следует сравнивать с путем, заданным в параметре `Path`.|  
|`InPath`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит элементы, обнаруженные по указанному пути.|  
|`OutOfPath`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит элементы, не обнаруженные по указанному пути.|  
|`Path`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает путь к папке для использования в качестве ссылки.|  
|`UpdateToAbsolutePaths`|Необязательный параметр типа `Boolean`.<br /><br /> Если true, для обеспечения абсолютности путей пути к выходным элементам нужно обновить.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `FindUnderPath` используется для определения наличия в файлах, содержащихся в элементе `MyFiles`, путей ниже указанного свойством `SearchPath`.  По завершении выполнения задачи элемент `FilesNotFoundInPath` содержит файл `File1.txt`, а элемент `FilesFoundInPath` содержит файл `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)