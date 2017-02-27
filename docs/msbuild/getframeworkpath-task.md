---
title: "Задача GetFrameworkPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath - задача [MSBuild]"
  - "MSBuild, GetFrameworkPath - задача"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Задача GetFrameworkPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Извлечение пути к сборкам [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `GetFrameworkPath`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`FrameworkVersion11Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к сборкам .NET Framework 1.1, если они присутствуют.  В противном случае возвращает значение `null`.|  
|`FrameworkVersion20Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к сборкам .NET Framework 2.0, если они присутствуют.  В противном случае возвращает значение `null`.|  
|`FrameworkVersion30Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к сборкам .NET Framework 3.0, если они присутствуют.  В противном случае возвращает значение `null`.|  
|`FrameworkVersion35Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к сборкам .NET Framework 3.5, если они присутствуют.  В противном случае возвращает значение `null`.|  
|`FrameworkVersion40Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к сборкам .NET Framework 4.0, если они присутствуют.  В противном случае возвращает значение `null`.|  
|`Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к наиболее свежим сборкам .NET Framework, если они доступны.  В противном случае возвращает значение `null`.|  
  
## Заметки  
 Если установлено несколько версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], задача вернет версию, которая предназначена для работы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `GetFrameworkPath` используется для сохранения пути к [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в свойстве `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)