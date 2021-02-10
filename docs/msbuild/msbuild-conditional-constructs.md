---
title: Условные конструкции MSBuild | Документы Майкрософт
description: Сведения о доступности в MSBuild механизма для обработки условий с использованием элементов Choose, When и Otherwise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10b26e9bdc0c632f924a29cd2ad09c21f8048d31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919141"
---
# <a name="msbuild-conditional-constructs"></a>Условные конструкции MSBuild

MSBuild предоставляет механизм для обработки условий "либо — либо" с помощью элементов [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) и [Otherwise](../msbuild/otherwise-element-msbuild.md).

## <a name="use-the-choose-element"></a>Использование элемента Choose

 Элемент `Choose` содержит ряд элементов `When` с атрибутами `Condition`, которые проверяются в порядке сверху вниз, пока один из них не даст значение `true`. Если значение `true` дают несколько элементов `When`, используется только первый из них. Если ни одно из условий элемента `When` не дает значение `true`, вычисляется элемент `Otherwise` (при его наличии).

 Элементы `Choose` можно использовать в качестве дочерних для элементов `Project`, `When` и `Otherwise`. Элементы `When` и `Otherwise` могут иметь дочерние элементы `ItemGroup`, `PropertyGroup` или `Choose`.

## <a name="example"></a>Пример

 Следующий пример использует элементы `Choose` и `When` для обработки условий "либо-либо". Свойства и элементы для проекта задаются в зависимости от значения свойства `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

В этом примере используется условие для константы компилятора `DEFINED_CONSTANT`. Настройки содержатся в свойстве `DefinedConstants`. Для сопоставления с конкретной константой в списке, элементы которого разделяются точкой с запятой, используется регулярное выражение.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>См. также

- [Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Элемент When (MSBuild)](../msbuild/when-element-msbuild.md)
- [Элемент Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
