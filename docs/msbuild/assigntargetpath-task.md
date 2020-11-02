---
title: Задача AssignTargetPath | Документы Майкрософт
description: Использование задачи AssignTargetPath MSBuild для принятия списка файлов и добавления атрибутов TargetPath, если они еще не заданы.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e56bb8817551e24d1b5aceef2f571e35f1db43e
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353334"
---
# <a name="assigntargetpath-task"></a>Задача AssignTargetPath

Эта задача принимает список файлов и добавляет атрибуты `<TargetPath>`, если они еще не указаны.

## <a name="task-parameters"></a>Параметры задачи

В следующей таблице приводятся параметры задачи `AssignTargetPath` .

|Параметр|Описание|
|---------------|-----------------|
|`RootFolder`|Необязательный входной параметр `string`.<br /><br /> Содержит путь к папке с целевыми ссылками.|
|`Files`|Необязательный входной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит исходный список файлов.|
|`AssignedFiles`|Необязательно<br /><br /> Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Содержит итоговый список файлов.|

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

Следующий пример выполняет задачу `AssignTargetPath`, чтобы настроить проект.

```xml
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

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
