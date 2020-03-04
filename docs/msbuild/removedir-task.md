---
title: Задача RemoveDir | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26a6feeca7c89a67e7dd51bd0a1f99a182ffac59
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632801"
---
# <a name="removedir-task"></a>RemoveDir - задача

Удаляет указанные каталоги и все содержащиеся в них файлы и подкаталоги.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `RemoveDir` .

|Параметр|Описание|
|---------------|-----------------|
|`Directories`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает каталоги для удаления.|
|`RemovedDirectories`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит каталоги, которые были успешно удалены.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 Следующий пример удаляет каталоги, указанные в свойствах `OutputDirectory` и `DebugDirectory`. Эти пути указываются относительно каталога проекта.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
        <DebugDirectory>\Debug\</DebugDirectory>
    </PropertyGroup>

    <Target Name="RemoveDirectories">
        <RemoveDir
            Directories="$(OutputDirectory);$(DebugDirectory)" />
    </Target>

</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
