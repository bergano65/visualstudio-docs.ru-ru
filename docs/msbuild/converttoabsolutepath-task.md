---
title: "Задача ConvertToAbsolutePath | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8637ba20fd6d5525293d9346c85a3365d700c3f8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="converttoabsolutepath-task"></a>Задача ConvertToAbsolutePath
Преобразует относительный путь или ссылку в абсолютный путь.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `ConvertToAbsolutePath`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Paths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список относительных путей, подлежащих преобразованию в абсолютные пути.|  
|`AbsolutePaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Список абсолютных путей для переданных элементов.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)