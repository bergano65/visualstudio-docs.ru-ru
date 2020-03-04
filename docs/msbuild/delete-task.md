---
title: Задача Delete | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634283"
---
# <a name="delete-task"></a>Delete - задача

Удаляет указанные файлы.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи `Delete` .

|Параметр|Описание|
|---------------|-----------------|
|`DeletedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает файлы, которые были успешно удалены.|
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для удаления.|
|`TreatErrorsAsWarnings`|Необязательный параметр `Boolean`.<br /><br /> Если `true`, ошибки регистрируются как предупреждения. Значение по умолчанию — `false`.|

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Будьте осторожны при использовании подстановочных знаков в задаче `Delete`. Вы можете случайно удалить не те файлы, используя такие выражения, как `$(SomeProperty)\**\*.*` или `$(SomeProperty)/**/*.*`, особенно если для свойства задана пустая строка. В этом случае параметр `Files` может затронуть корень диска и удалить гораздо больше, чем требовалось.

## <a name="example"></a>Пример

В следующем примере рассматривается удаление файла *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
