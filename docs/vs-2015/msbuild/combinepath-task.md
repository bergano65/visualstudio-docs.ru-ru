---
title: Задача CombinePath | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71176722443cc2e7f858bbfea85d526a4f4d772d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192690"
---
# <a name="combinepath-task"></a>Задача CombinePath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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



