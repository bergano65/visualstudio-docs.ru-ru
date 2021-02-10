---
title: Элемент Choose (MSBuild) | Документация Майкрософт
description: Используйте элемент Choose MSBuild, чтобы оценить дочерние элементы и выбрать один набор элементов ItemGroup или PropertyGroup для вычисления.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a3cb3ae9ef120954bb3c299cdf310a32da69845
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939517"
---
# <a name="choose-element-msbuild"></a>Элемент Choose (MSBuild)

Вычисляет дочерние элементы для выбора одного набора элементов `ItemGroup` и/или элементов `PropertyGroup` для вычисления.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Синтаксис

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Необязательный элемент.<br /><br /> Указывает блок кода `PropertyGroup` и элементы `ItemGroup` для оценки, если условия всех элементов `When` оценены как `false`. Элемент `Choose` может содержать ноль элементов `Otherwise` или один такой элемент, который должен быть последним.|
|[When](../msbuild/when-element-msbuild.md)|Обязательный элемент.<br /><br /> Указывает один из возможных блоков кода, который может выбрать элемент `Choose`. Элемент `When` может содержать один или несколько элементов `Choose`.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Otherwise](../msbuild/otherwise-element-msbuild.md) | Указывает блок кода, который должен быть выполнен, если условия всех элементов `When` оценены как `false`. |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта MSBuild. |
| [When](../msbuild/when-element-msbuild.md) | Указывает один из возможных блоков кода, который может выбрать элемент `Choose`. |

## <a name="remarks"></a>Remarks

 Элементы `Choose`, `When` и `Otherwise` используются совместно, чтобы обеспечить выбор одного блока кода для выполнения из множества доступных вариантов. См. дополнительные сведения об [условных конструкциях](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Пример

 Следующий проект использует элемент `Choose`, чтобы выбрать набор значений свойств, который будет задан в элементах `When`. Если атрибуты `Condition` обоих элементов `When` оцениваются как `false`, в элементе `Otherwise` задаются значения свойств.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>См. также раздел

- [Условные конструкции](../msbuild/msbuild-conditional-constructs.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
