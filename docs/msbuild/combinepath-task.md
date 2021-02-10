---
title: Задача CombinePath | Документация Майкрософт
description: Сведения о том, как с помощью задачи CombinePath MSBuild объединить указанные пути в один путь.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1eb27a311f1b61e3e36b4c9eaa65de7f3fd8f1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939504"
---
# <a name="combinepath-task"></a>CombinePath - задача

Объединяет указанные пути в единый путь.
## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры [задачи CombinePath](../msbuild/combinepath-task.md).


|Параметр|Описание|
|---------------|-----------------|
|`BasePath`|Обязательный параметр `String` .<br /><br /> Базовый путь для объединения с другими путями. Может представлять собой относительный, абсолютный путь или быть пустым.|
|`Paths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список отдельных путей, объединяемых с BasePath для получения объединенного пути. Пути могут быть как относительными, так и абсолютными.|
|`CombinedPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Объединенный путь, созданный этой задачей.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

 В следующем примере показано, как создать структуру выходной папки с помощью `CombinePath` для создания свойства `$(OutputDirectory)` путем объединения корневого пути `$(PublishRoot)`, сцепленного с `$(ReleaseDirectory)`, и списка вложенных папок `$(LangDirectories)`.

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

Единственным свойством, которое `CombinePath` допускает в качестве списка, является `Paths`. В этом случае выходные данные также являются списком. Таким образом, если `$(PublishRoot)` это *C:\Site1\\* , `$(ReleaseDirectory)` это *Release\\* , `@(LangDirectories)` это *en-us\;fr-fr\\* , тогда будут созданы следующие папки:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
