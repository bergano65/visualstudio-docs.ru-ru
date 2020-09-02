---
title: Задача AssignTargetPath | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7bf12e9f6c90ce544205370a8ed26440388b0a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187018"
---
# <a name="assigntargetpath-task"></a>Задача AssignTargetPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта задача принимает список файлов и добавляет атрибуты `<TargetPath>`, если они еще не указаны.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `AssignTargetPath`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`RootFolder`|Необязательный входной параметр `string`.<br /><br /> Содержит путь к папке с целевыми ссылками.|  
|`Files`|Необязательный входной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит исходный список файлов.|  
|`AssignedFiles`|Необязательно<br /><br /> Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Содержит итоговый список файлов.|  
  
## <a name="remarks"></a>Remarks  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример выполняет задачу `AssignTargetPath`, чтобы настроить проект.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
