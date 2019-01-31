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
ms.openlocfilehash: efae349037d6a826c4d267e12d901306eed7629b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758701"
---
# <a name="assigntargetpath-task"></a>Задача AssignTargetPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Эта задача принимает список файлов и добавляет атрибуты `<TargetPath>`, если они еще не указаны.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `AssignTargetPath`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`RootFolder`|Необязательный входной параметр `string`.<br /><br /> Содержит путь к папке с целевыми ссылками.|  
|`Files`|Необязательный входной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит исходный список файлов.|  
|`AssignedFiles`|Optional<br /><br /> Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Содержит итоговый список файлов.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
