---
title: "Задача ResolveManifestFiles | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 088af1d1ef0a83b695b0a36baaa424a4926f3112
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="resolvemanifestfiles-task"></a>Задача ResolveManifestFiles
Разрешает следующие элементы в процессе сборки в файлы для создания манифеста: элементы сборки, зависимости, вспомогательные элементы, содержимое, отладочные символы и документация.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ResolveManifestFiles` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Определяет имя манифеста развертывания.|  
|`EntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Определяет управляемую сборку или ссылку на манифест ClickOnce, являющуюся точкой входа в манифест.|  
|`ExtraFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет дополнительные файлы.|  
|`ManagedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет управляемые сборки.|  
|`NativeAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет машинные сборки.|  
|`OutputAssemblies`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет созданные сборки.|  
|`OutputDeploymentManifestEntryPoint`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет точку входа манифеста развертывания выходного файла.|  
|`OutputEntryPoint`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет точку входа выходного файла.|  
|`OutputFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет выходные файлы.|  
|`PublishFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет файлы публикации.|  
|`SatelliteAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет вспомогательные сборки.|  
|`SigningManifests`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, манифесты являются подписанными.|  
|`TargetCulture`|Необязательный параметр `String` .<br /><br /> Определяет целевой язык и региональные параметры для вспомогательных сборок.|  
|`TargetFrameworkVersion`|Необязательный параметр `String` .<br /><br /> Определяет целевую версию .NET Framework.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)