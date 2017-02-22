---
title: "Задача AssignTargetPath | Microsoft Docs"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача AssignTargetPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта задача принимает список файлов и добавляет `<TargetPath>` атрибуты, если они уже не указаны.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `AssignTargetPath`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`RootFolder`|Необязательный входной параметр `string`.<br /><br /> Путь к папке, содержащей целевые ссылки.|  
|`Files`|Необязательный входной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит входящий список файлов.|  
|`AssignedFiles`|Необязательно<br /><br /> Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`<br /><br /> Содержит результирующий список файлов.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере выполняется задача `AssignTargetPath` для настройки проекта.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)