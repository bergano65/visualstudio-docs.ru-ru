---
title: Преобразования MSBuild | Документы Майкрософт
description: Узнайте, как MSBuild использует преобразования "один к одному" для преобразования одного списка элементов в другой, позволяя более эффективно создавать проекты.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba6a71373026a5a41905efc7c91520a9f6b7c5c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878211"
---
# <a name="msbuild-transforms"></a>Преобразования MSBuild

Преобразование — это однозначное преобразование одного списка элементов в другой. Помимо возможности преобразования списков элементов в проекте, преобразование позволяет целевому объекту определить прямое сопоставление входных и выходных данных. Этот раздел описывает преобразования и то, как MSBuild использует их для более эффективной сборки проектов.

## <a name="transform-modifiers"></a>Модификаторы преобразования

Преобразования не являются произвольными, они ограничены специальным синтаксисом, в котором все модификаторы преобразования должны иметь формат %(\<ItemMetaDataName>). Метаданные элементов можно использовать в качестве модификаторов преобразования. Сюда входят стандартные метаданные элементов, назначаемые каждому элементу при создании. Список стандартных метаданных элементов см. в статье [Общеизвестные метаданные элементов MSBuild](../msbuild/msbuild-well-known-item-metadata.md).

В приведенном ниже примере список файлов *RESX* преобразуется в список файлов *RESOURCES*. Модификатор преобразования %(filename) указывает, что каждый файл *RESOURCES* имеет то же имя, что и соответствующий файл *RESX*.

```xml
@(RESXFile->'%(filename).resources')
```

Например, если в списке элементов @(RESXFile) содержатся элементы *Form1.resx*, *Form2.resx* и *Form3.resx*, выходными элементами в преобразованном списке будут *Form1.resources*, *Form2.resources* и *Form3.resources*.

> [!NOTE]
> Вы можете указать настраиваемый разделитель для преобразованного списка элементов точно так же, как и для стандартного списка элементов. Например, чтобы разделить преобразованный список элементов с помощью запятой (,), а не используемой по умолчанию точки с запятой (;), используйте следующий код XML: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Использование нескольких модификаторов

 Выражение преобразования может содержать несколько модификаторов, которые можно объединять в любом порядке, кроме того, они могут повторяться. В следующем примере изменяется имя каталога, содержащего файлы, однако файлы сохраняют исходное имя и расширение.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Например, если в списке элементов `RESXFile` содержатся элементы *Project1\Form1.resx*, *Project1\Form2.resx* и *Project1\Form3.text*, выходными элементами в преобразованном списке будут *Toolset\Form1.resx*, *Toolset\Form2.resx* и *Toolset\Form3.text*.

## <a name="dependency-analysis"></a>Анализ зависимостей

 Преобразование обеспечивает однозначное сопоставление между преобразованным и исходным списками элементов. Таким образом, если целевой объект создает выходные данные, полученные путем преобразования входных файлов, MSBuild может проанализировать метки времени входных и выходных данных и решить, следует ли пропустить целевой объект, выполнить его сборку или частично перестроить.

 В [задаче Copy](../msbuild/copy-task.md) в следующем примере каждый файл в списке элементов `BuiltAssemblies` сопоставляется с файлом в папке назначения задачи, указанной с помощью преобразования в атрибуте `Outputs`. Если изменяется файл в списке элементов `BuiltAssemblies`, задача `Copy` выполняется только для измененного файла, а все остальные файлы пропускаются. Дополнительные сведения об анализе зависимостей и использовании преобразований см. в статье [Практическое руководство. Инкрементная сборка](../msbuild/how-to-build-incrementally.md).

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>Пример

### <a name="description"></a>Описание

 Следующий пример показывает файл проекта MSBuild, использующий преобразования. В этом примере предполагается, что в каталоге *c:\sub0\sub1\sub2\sub3* есть только один *XSD-файл*, а рабочим каталогом является *c:\sub0*.

### <a name="code"></a>Код

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>Комментарии

 В этом примере выводятся следующие данные:

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>См. также

- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Практическое руководство. Инкрементная сборка](../msbuild/how-to-build-incrementally.md)
