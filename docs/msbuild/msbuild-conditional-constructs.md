---
title: "Условные конструкции MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> - элемент [MSBuild]"
  - "<Otherwise> - элемент [MSBuild]"
  - "<When> - элемент [MSBuild]"
  - "Choose - элемент [MSBuild]"
  - "условные конструкции [MSBuild]"
  - "MSBuild, условные конструкции"
  - "Otherwise - элемент [MSBuild]"
  - "When - элемент [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Условные конструкции MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет механизм для обработки ситуации выбора с помощью элементов [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) и [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## Использование элемента Choose  
 Элемент `Choose` содержит последовательность элементов `When` с атрибутами `Condition`, которые проверяются сверху вниз, пока для одного из них не будет получен результат `true`.  Если более чем для одного элемента `When` получен результат `true`, используется только первый элемент.  Элемент `Otherwise`, если он есть, будет обрабатываться в случае, если ни для одного условия в элементах  `When` не был получен результат `true`.  
  
 Элементы `Choose` можно использовать в качестве дочерних элементов для элементов `Project`, `When` и `Otherwise`.  Элементы `When` и `Otherwise` могут иметь дочерние элементы `ItemGroup`, `PropertyGroup` или `Choose`.  
  
## Пример  
 В следующем примере элементы `Choose` и `When` используются для обработки ситуации выбора.  Свойства и элементы для данного проекта устанавливаются в зависимости от значения свойства `Configuration`.  
  
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
  
## См. также  
 [Элемент Choose \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [Элемент When \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Элемент Otherwise \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)