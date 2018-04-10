---
title: Задача ResolveNonMSBuildProjectOutput | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e451f301aa7a5bb4ac8f176d9ebe59fa66b0f662
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>Задача ResolveNonMSBuildProjectOutput
Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ResolveNonMSBuildProjectOutput` .  
  
|Параметр|Описание|  
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