---
title: "Задача RequiresFramework35SP1Assembly | Microsoft Docs"
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
  - "MSBuild, RequiresFramework35SP1Assembly - задача"
  - "RequiresFramework35SP1Assembly - задача [MSBuild]"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача RequiresFramework35SP1Assembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет, требуется ли для приложения платформа .NET Framework 3.5 с пакетом обновления 1 \(SP1\).  
  
## Параметры  
 В следующей таблице описаны параметры задачи `RequiresFramework35SP1Assembly`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Assemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые имеются ссылки в приложении.|  
|`CreateDesktopShortcut`|Необязательный параметр типа `Boolean`.<br /><br /> Если `true`, во время установки на рабочем столе создается ярлык.|  
|`DeploymentManifestEntryPoint`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает имя файла манифеста приложения.|  
|`EntryPoint`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> задает сборку, которую нужно выполнить при запуске приложения.|  
|`ErrorReportUrl`|Необязательный параметр типа `String`.<br /><br /> задает веб\-сайт, который отображается в диалоговых окнах, которые выводятся во время установки ClickOnce.|  
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет список файлов, которые будут развернуты при публикации приложения.|  
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые имеются ссылки в проекте.|  
|`RequiresMinimumFramework35SP1`|Необязательный выходной параметр `Boolean`.<br /><br /> Если значение `true`, для приложения требуется платформа .NET Framework 3.5 с пакетом обновления 1 \(SP1\).|  
|`SigningManifests`|Необязательный выходной параметр `Boolean`.<br /><br /> Если значение `true`, манифест ClickOnce подписан.|  
|`SuiteName`|Необязательный параметр типа `String`.<br /><br /> Указывает имя папки в меню **Пуск**, в которую будет установлено приложение.|  
|`TargetFrameworkVersion`|Необязательный параметр типа `String`.<br /><br /> задает версию платформы .NET Framework, для которой предназначено данное приложение.|  
  
## Заметки  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)