---
title: Условные конструкции MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ade8344b5f4189e9588fc8e75ef88fa5cf8f8c5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080201"
---
# <a name="msbuild-conditional-constructs"></a>Условные конструкции MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет механизм для обработки условий "либо-либо" с помощью элементов [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) и [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Элемент When (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Элемент Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)