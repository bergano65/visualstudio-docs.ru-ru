---
title: Задача ResolveManifestFiles | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ba088b91496c633afe34c20e40c12ded7d2279b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161363"
---
# <a name="resolvemanifestfiles-task"></a>Задача ResolveManifestFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Разрешает следующие элементы в процессе сборки в файлы для создания манифеста: элементы сборки, зависимости, вспомогательные элементы, содержимое, отладочные символы и документация.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ResolveManifestFiles`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет имя манифеста развертывания.|  
|`EntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет управляемую сборку или ссылку на манифест ClickOnce, являющуюся точкой входа в манифест.|  
|`ExtraFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет дополнительные файлы.|  
|`ManagedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет управляемые сборки.|  
|`NativeAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет машинные сборки.|  
|`OutputAssemblies`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет созданные сборки.|  
|`OutputDeploymentManifestEntryPoint`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет точку входа манифеста развертывания выходного файла.|  
|`OutputEntryPoint`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет точку входа выходного файла.|  
|`OutputFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет выходные файлы.|  
|`PublishFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет файлы публикации.|  
|`SatelliteAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет вспомогательные сборки.|  
|`SigningManifests`|Необязательный параметр `Boolean`.<br /><br /> Если `true`, манифесты являются подписанными.|  
|`TargetCulture`|Необязательный параметр `String`.<br /><br /> Определяет целевой язык и региональные параметры для вспомогательных сборок.|  
|`TargetFrameworkVersion`|Необязательный параметр `String`.<br /><br /> Определяет целевую версию .NET Framework.|  
  
## <a name="remarks"></a>Remarks  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
