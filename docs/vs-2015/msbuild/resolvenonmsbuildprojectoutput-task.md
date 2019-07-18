---
title: Задача ResolveNonMSBuildProjectOutput | Документы Майкрософт
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
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aaf99affe9c29762aa8b47ea76419da429089b7c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156147"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Задача ResolveNonMSBuildProjectOutput
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ResolveNonMSBuildProjectOutput` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Необязательный параметр `String` .<br /><br /> Задает XML-строку, содержащую разрешенные выходные данные проекта.|  
|`ProjectReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает ссылки проекта.|  
|`ResolvedOutputPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список путей разрешенных ссылок (и сохраняет исходные атрибуты ссылок проекта).|  
|`UnresolvedProjectReferences`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список элементов ссылок проекта, которые не удалось разрешить с помощью предварительно разрешенного списка выходных данных.<br /><br /> Так как Visual Studio предварительно разрешает только проекты, отличные от MSBuild, ссылки проекта в этом списке имеют формат MSBuild.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
