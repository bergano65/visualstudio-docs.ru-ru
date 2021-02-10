---
title: Практическое руководство. Выбор файлов для сборки | Документация Майкрософт
description: Сведения о том, как выбрать файлы для сборки в файле проекта MSBuild, указав каждый файл отдельно или используя подстановочные знаки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f324fb3999c94d8f26e329859e095f31740c76c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914234"
---
# <a name="how-to-select-the-files-to-build"></a>Практическое руководство. Выбор файлов для сборки

При создании проекта, содержащего несколько файлов, можно указать каждый файл отдельно в файле проекта либо можно использовать подстановочные знаки, чтобы включить все файлы в одном каталоге или наборе вложенных каталогов.

## <a name="specify-inputs"></a>Указание входных данных

Элементы представляют собой входные данные для сборки. Дополнительные сведения об элементах см. в разделе [Элементы](../msbuild/msbuild-items.md).

Чтобы включить файлы в сборку, их необходимо включить в список элементов в файле проекта MSBuild. В список элементов можно добавить несколько файлов, как по отдельности, так и с помощью подстановочных знаков (чтобы включить несколько файлов одновременно).

#### <a name="to-declare-items-individually"></a>Объявление отдельных элементов

- Используйте атрибуты `Include`, аналогичные следующим.

    `<CSFile Include="form1.cs"/>`

    or

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Если элементы в коллекции элементов не находятся в том же каталоге, что и файл проекта, необходимо указать полный или относительный путь к элементу. Например: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Объявление нескольких элементов

- Используйте атрибуты `Include`, аналогичные следующим.

    `<CSFile Include="form1.cs;form2.cs"/>`

    or

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Указание входных данных с помощью подстановочных знаков

Подстановочные знаки можно использовать для рекурсивного включения всех файлов или только определенных файлов из подкаталогов в качестве входных данных для сборки. Дополнительные сведения о подстановочных знаках см. в разделе [Элементы](../msbuild/msbuild-items.md).

В примерах ниже за основу взят проект, в котором содержатся графические файлы в следующих каталогах и подкаталогах (файл проекта находится в каталоге *Project*):

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Включение всех *JPG*-файлов в каталоге *Images* и подкаталогах

- Используйте следующий атрибут `Include`.

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Включение всех *JPG*-файлов, начинающихся со слога *img*

- Используйте следующий атрибут `Include`.

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Включение всех файлов в каталогах с именами, которые оканчиваются слогом *jpgs*

- Используйте один из следующих атрибутов `Include`.

    `Include="Images\**\*jpgs\*.*"`

    or

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Передача элементов в задачу

В файле проекта используйте в задачах запись @(), чтобы указать весь список элементов в качестве входных данных для сборки. Эту запись можно использовать при перечислении файлов по отдельности или при использовании подстановочных знаков.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Использование всех файлов Visual C# или Visual Basic в качестве входных данных

- Используйте атрибуты `Include`, аналогичные следующим.

    `<CSC Sources="@(CSFile)">...</CSC>`

    or

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Чтобы указать входные данные для сборки, нужно использовать подстановочные знаки в элементах; с помощью атрибута `Sources` невозможно указать входные данные в задачах MSBuild, таких как [Csc](../msbuild/csc-task.md) или [Vbc](../msbuild/vbc-task.md). Следующий пример недопустим в файле проекта.
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>Пример 1

В примере ниже показан проект, в котором все входные файлы включены по отдельности.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example-2"></a>Пример 2

В примере ниже используется подстановочный знак для включения всех *CS*-файлов.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>См. также статью

- [Практическое руководство. Исключение файлов из сборки](../msbuild/how-to-exclude-files-from-the-build.md)
- [Элементы](../msbuild/msbuild-items.md)
