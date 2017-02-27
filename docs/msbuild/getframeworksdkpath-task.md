---
title: "Задача GetFrameworkSdkPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath - задача [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath - задача"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Задача GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Извлечение пути к [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `GetFrameworkSdkPath`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`FrameworkSdkVersion20Path`|Необязательный выходной параметр типа `String`, доступный только для чтения.<br /><br /> Возвращает путь к сборкам .NET SDK 2.0, если он присутствует.  В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Необязательный выходной параметр типа `String`, доступный только для чтения.<br /><br /> Возвращает путь к сборкам .NET SDK 3.5, если он присутствует.  В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Необязательный выходной параметр типа `String`, доступный только для чтения.<br /><br /> Возвращает путь к сборкам .NET SDK 4.0, если он присутствует.  В противном случае возвращает значение `String.Empty`.|  
|`Path`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит путь к наиболее свежему пакету SDK .NET Framework, если он присутствуют.  В противном случае возвращает значение `String.Empty`.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `GetFrameworkSdkPath` используется для сохранения пути к [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] в свойстве `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)