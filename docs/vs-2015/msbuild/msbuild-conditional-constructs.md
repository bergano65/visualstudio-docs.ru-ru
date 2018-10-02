---
title: Условные конструкции MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7997db7fc5c7dd866de8f9d573779ead29e5e9d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558850"
---
# <a name="msbuild-conditional-constructs"></a>Условные конструкции MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [условные конструкции MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-conditional-constructs).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] предоставляет механизм для обработки условий "либо-либо" с помощью элементов [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) и [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## <a name="using-the-choose-element"></a>Использование элемента Choose  
 Элемент `Choose` содержит ряд элементов `When` с атрибутами `Condition`, которые проверяются в порядке сверху вниз, пока один из них не даст значение `true`. Если значение `true` дают несколько элементов `When`, используется только первый из них. Если ни одно из условий элемента `When` не дает значение `true`, вычисляется элемент `Otherwise` (при его наличии).  
  
 Элементы `Choose` можно использовать в качестве дочерних для элементов `Project`, `When` и `Otherwise`. Элементы `When` и `Otherwise` могут иметь дочерние элементы `ItemGroup`, `PropertyGroup` или `Choose`.  
  
## <a name="example"></a>Пример  
 Следующий пример использует элементы `Choose` и `When` для обработки условий "либо-либо". Свойства и элементы для проекта задаются в зависимости от значения свойства `Configuration`.  
  
```  
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



