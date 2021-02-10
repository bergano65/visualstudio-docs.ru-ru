---
title: Задача ResourcesGenerator | Документация Майкрософт
description: Узнайте, как в MSBuild используется задача ResourcesGenerator для внедрения одного или нескольких ресурсов в файл RESOURCES.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a26c8bfc29ca985a725deea6c75b14d68abb9eb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937892"
---
# <a name="resourcesgenerator-task"></a>Задача ResourcesGenerator

Задача <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> внедряет один или несколько ресурсов (*JPG*, *ICO*, *BMP* и XAML в двоичном формате, а также другие типы расширений) в файл *RESOURCES*.

## <a name="task-parameters"></a>Параметры задачи

|Параметр|Описание|
|---------------|-----------------|
|`OutputPath`|Обязательный параметр **String**.<br /><br /> Определяет абсолютный путь выходного каталога. Если путь не является абсолютным, он интерпретируется относительно корневого каталога проекта.|
|`OutputResourcesFile`|Обязательный параметр вывода **ITaskItem[]**.<br /><br /> Определяет путь и имя для созданного файла *RESOURCES*. Если путь не является абсолютным, файл *RESOURCES* создается относительно корневого каталога проекта.|
|`ResourcesFiles`|Обязательный параметр **ITaskItem[]** .<br /><br /> Определяет один или несколько ресурсов для внедрения в созданный файл *RESOURCES*.|

## <a name="example"></a>Пример

 Следующий пример создает файл *RESOURCES* с одним ресурсом *BMP*. Ресурс *BMP* создается в каталоге, который расположен относительно корневого каталога проекта.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)