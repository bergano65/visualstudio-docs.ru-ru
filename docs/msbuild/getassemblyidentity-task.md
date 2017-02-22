---
title: "Задача GetAssemblyIdentity | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetAssemblyIdentity - задача [MSBuild]"
  - "MSBuild, GetAssemblyIdentity - задача"
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача GetAssemblyIdentity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Извлечение идентификаторов сборок из указанных файлов и вывод сведений об удостоверении.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `GetAssemblyIdentity`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Assemblies`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Этот параметр содержит извлеченные идентификаторы сборок.|  
|`AssemblyFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Этот параметр указывает файлы, из которых требуется извлечь идентификаторы.|  
  
## Заметки  
 Элементы, выводимые параметром `Assemblies`, содержат записи элементов метаданных с именами `Version`, `PublicKeyToken` и `Culture`.  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере демонстрируется извлечение идентификаторов файлов, заданных в элементе `MyAssemblies`, и их вывод в элемент `MyAssemblyIdentities`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)