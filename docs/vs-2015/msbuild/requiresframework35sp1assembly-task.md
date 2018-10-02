---
title: Задача RequiresFramework35SP1Assembly | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0ffc3b685314983949026a67f9be95f0fce1245
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563287"
---
# <a name="requiresframework35sp1assembly-task"></a>Задача RequiresFramework35SP1Assembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [requiresframework35sp1assembly-задача](https://docs.microsoft.com/visualstudio/msbuild/requiresframework35sp1assembly-task).  
  
  
Определяет, требуется ли для приложения платформа .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `RequiresFramework35SP1Assembly` .  
  
|Параметр|Описание|  
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



