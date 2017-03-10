---
title: "Задача CombinePath | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a6fb322adceef7947cbb671d04e72169e06f74a7
ms.lasthandoff: 02/22/2017

---
# <a name="combinepath-task"></a>Задача CombinePath
Объединяет указанные пути в единый путь.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры [задачи CombinePath](../msbuild/combinepath-task.md).  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`BasePath`|Обязательный параметр `String`.<br /><br /> Базовый путь для объединения с другими путями. Может представлять собой относительный, абсолютный путь или быть пустым.|  
|`Paths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список отдельных путей, объединяемых с BasePath для получения объединенного пути. Пути могут быть как относительными, так и абсолютными.|  
|`CombinedPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Объединенный путь, созданный этой задачей.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует их от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
