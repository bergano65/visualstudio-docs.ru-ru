---
title: "Задача CombinePath | Документация Майкрософт"
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f67014faf67d0855ba7e800ad66e014eb665efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="combinepath-task"></a>Задача CombinePath
Объединяет указанные пути в единый путь.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры [задачи CombinePath](../msbuild/combinepath-task.md).  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`BasePath`|Обязательный параметр `String` .<br /><br /> Базовый путь для объединения с другими путями. Может представлять собой относительный, абсолютный путь или быть пустым.|  
|`Paths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список отдельных путей, объединяемых с BasePath для получения объединенного пути. Пути могут быть как относительными, так и абсолютными.|  
|`CombinedPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Объединенный путь, созданный этой задачей.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)