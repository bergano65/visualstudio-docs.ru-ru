---
title: "Задача GetReferenceAssemblyPaths | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача GetReferenceAssemblyPaths
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возвращает пути к базовым сборкам для различных версий .NET Framework.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `GetReferenceAssemblyPaths`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`ReferenceAssemblyPaths`|Необязательный выходной параметр `String[]`.<br /><br /> Возвращает путь, основанный на параметре `TargetFrameworkMoniker` .  Если `TargetFrameworkMoniker` равен null или является пустым, этот путь будет `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Необязательный выходной параметр `String[]`.<br /><br /> Возвращает путь на основе параметра `TargetFrameworkMoniker`, без учета профильной части моникера.  Если `TargetFrameworkMoniker` равен null или является пустым, этот путь будет `String.Empty`.|  
|`TargetFrameworkMoniker`|Необязательный параметр типа `String`.<br /><br /> Указывает моникер требуемой версии .NET Framework, связанный с путями к базовой сборке.|  
|`RootPath`|Необязательный параметр типа `String`.<br /><br /> Задает Корневой путь, который необходимо использовать для создания пути к базовой сборке|  
|`BypassFrameworkInstallChecks`|Необязательный параметр типа [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True).<br /><br /> Если `true`, пропускает основные проверки, которые по умолчанию проводит `GetReferenceAssemblyPaths`, чтобы убедиться, что установлены нужные платформы среды выполнения в зависимости от целевой платформы.|  
|`TargetFrameworkMonikerDisplayName`|Необязательный выходной параметр типа `String`.<br /><br /> Задает отображаемое имя для моникера требуемой версии .NET Framework.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)