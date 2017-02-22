---
title: "Задача CreateProperty | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty - задача [MSBuild]"
  - "MSBuild, CreateProperty - задача"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача CreateProperty
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Заполняет свойства переданными значениями.  Это позволяет копировать значения из одного свойства или строки в другое свойство или строку.  
  
## Атрибуты  
 В следующей таблице описаны параметры задачи `CreateProperty`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Value`|Необязательный выходной параметр типа `String`.<br /><br /> Задает значение, которое требуется скопировать в новое свойство.|  
|`ValueSetByTask`|Необязательный выходной параметр типа `String`.<br /><br /> Содержит то же значение, что и параметр `Value`.  Используйте этот параметр только в том случае, когда требуется избежать установки выходного свойства сборочной системой [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], когда внешний целевой объект пропускается при сборке из\-за того, что выходные данные имеют последнюю версию.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `CreateProperty` используется для создания свойства `NewFile`, содержащего сочетание значений свойств `SourceFilename` и `SourceFileExtension`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 После выполнения проекта свойство `NewFile` примет значение `Module1.vb`.  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)