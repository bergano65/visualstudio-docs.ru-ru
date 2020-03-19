---
title: Задача Unzip | Документы Майкрософт
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631514"
---
# <a name="unzip-task"></a>Задача Unzip

Распаковывает *ZIP-архив* в заданное расположение.

>[!NOTE]
>Задача `Unzip` доступна только в MSBuild 15.8 и более поздних версий.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `Unzip`.

|Параметр|Description|
|---------------|-----------------|
|`DestinationFolder`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Указывает папку назначения для распаковки файла.|
|`OverwriteReadOnlyFiles`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, перезаписывает файлы, доступные только для чтения. По умолчанию равен `false`.|
|`SkipUnchangedFiles`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, пропускает распаковку файлов, которые не изменились. По умолчанию равен `true`. В задаче `Unzip` неизмененными считаются файлы одного размера с одинаковым временем последнего изменения.|
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает один или несколько распаковываемых файлов. При указании нескольких файлов они распаковываются по очереди одну папку.|

## <a name="remarks"></a>Remarks

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 В следующем примере распаковывается архив и перезаписываются файлы только для чтения.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
