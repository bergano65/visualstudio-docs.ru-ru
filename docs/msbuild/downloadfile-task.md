---
title: Задача DownloadFile | Документы Майкрософт
description: Сведения о параметрах задачи DownloadFile MSBuild, которая скачивает указанные файлы с использованием протокола HTTP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c68b468cac63d556e9757210c8ce2933d94cba6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877217"
---
# <a name="downloadfile-task"></a>Задача DownloadFile

Загружает указанные файлы, используя протокол HTTP.

>[!NOTE]
>Задача DownloadFile доступна только в MSBuild 15.8 и более поздних версий.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи `DownloadFile` .

|Параметр|Описание|
|---------------|-----------------|
|`DestinationFileName`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Имя, используемое для загруженного файла.  По умолчанию имя файла получается от `SourceUrl` или удаленного сервера.|
|`DestinationFolder`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает папку назначения для загрузки файла.  Если папка не существует, она создается.|
|`DownloadedFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает файл, который вы загрузили.|
|`Retries`|Необязательный параметр `Int32`.<br /><br /> Задает количество попыток загрузки, если предыдущие попытки не удались. По умолчанию установлен нуль.|
|`RetryDelayMilliseconds`|Необязательный параметр `Int32`.<br /><br /> Определяет задержку в миллисекундах между попытками. По умолчанию — 5000.|
|`SkipUnchangedFiles`|Необязательный параметр `Boolean`.<br /><br /> При значении `true` пропускает загрузку файлов, которые не изменились. По умолчанию — `true`. В задаче `DownloadFile` неизмененными считаются файлы одного размера с одинаковым временем последнего изменения по данным удаленного сервера. <br /><br />**Примечание.** Не все HTTP-серверы указывают дату последнего изменения файла, что приведет к его повторной загрузке.|
|`SourceUrl`|Обязательный параметр `String`.<br /><br /> Указывает URL-адрес для загрузки.|

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

В следующем примере файл загружается и включается в элементы `Content` до сборки проекта.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
