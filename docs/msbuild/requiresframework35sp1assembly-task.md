---
title: "Задача RequiresFramework35SP1Assembly | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9f3a0ad2f5948319ef5de81577999787eeb0af71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="requiresframework35sp1assembly-task"></a>Задача RequiresFramework35SP1Assembly
Определяет, требуется ли для приложения платформа .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `RequiresFramework35SP1Assembly` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Assemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые в приложении есть ссылки.|  
|`CreateDesktopShortcut`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, создает значок ярлыка на рабочем столе во время установки.|  
|`DeploymentManifestEntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает имя файла манифеста для приложения.|  
|`EntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает сборку, которую следует выполнить при запуске приложения.|  
|`ErrorReportUrl`|Необязательный параметр `String` .<br /><br /> Указывает веб-сайт, который отображается в диалоговых окнах во время установок ClickOnce.|  
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает список файлов, которые будут развернуты при публикации приложения.|  
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые в проекте есть ссылки.|  
|`RequiresMinimumFramework35SP1`|Необязательный выходной параметр `Boolean`.<br /><br /> Если задано значение `true`, для приложения требуется платформа .NET Framework 3.5 с пакетом обновления 1 (SP1).|  
|`SigningManifests`|Необязательный выходной параметр `Boolean`.<br /><br /> Если задано значение `true`, манифесты ClickOnce подписаны.|  
|`SuiteName`|Необязательный параметр `String` .<br /><br /> Задает имя папки в меню **Пуск**, куда будет установлено приложение.|  
|`TargetFrameworkVersion`|Необязательный параметр `String` .<br /><br /> Задает версию платформы .NET Framework, для которой предназначено приложение.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)