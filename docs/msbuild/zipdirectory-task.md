---
title: Задача ZipDirectory | Документы Майкрософт
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c9a51fe097eb110e44b3f4bd932a26f4efb6ea6
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630643"
---
# <a name="zipdirectory-task"></a>Задача ZipDirectory

Создает *ZIP-архив* из содержимого каталога.

>[!NOTE]
>Задача `ZipDirectory` доступна только в MSBuild 15.8 и более поздних версий.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `ZipDirectory` .

|Параметр|Описание|
|---------------|-----------------|
|`DestinationFile`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Полный путь к создаваемому *ZIP-файлу*.|
|`Overwrite`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, пропускает целевой файл, который будет перезаписан при его наличии. По умолчанию — `false`.|
|`SourceDirectory`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает каталог, из которого создается *ZIP-архив*.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 В следующем примере создается *ZIP-архив* из каталога выходных данных после сборки проекта.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
