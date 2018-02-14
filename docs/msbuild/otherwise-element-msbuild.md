---
title: "Элемент Otherwise (MSBuild) | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e0b824b8be8b3697673d0d1f09a20b6a7c1cee58
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="otherwise-element-msbuild"></a>Элемент Otherwise (MSBuild)
Указывает блок кода, который должен быть выполнен, только если условия всех элементов `When` оценены как `false`.  

 \<Проект>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>Синтаксис  

```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  
 Отсутствует.  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Необязательный элемент.<br /><br /> Вычисляет дочерние элементы, чтобы выбрать один раздел кода для выполнения. Элемент `Otherwise` может содержать любое число элементов `Choose`, включая ноль.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор определенных пользователем элементов [Item](../msbuild/item-element-msbuild.md). Элемент `Otherwise` может содержать любое число элементов `ItemGroup`, включая ноль.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор определенных пользователем элементов [Property](../msbuild/property-element-msbuild.md). Элемент `Otherwise` может содержать любое число элементов `PropertyGroup`, включая ноль.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Вычисляет дочерние элементы, чтобы выбрать один раздел кода для выполнения.|  

## <a name="remarks"></a>Примечания  
 Элемент `Choose` может содержать только один элемент `Otherwise`, который должен быть последним.  

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

## <a name="see-also"></a>См. также  
 [Условные конструкции](../msbuild/msbuild-conditional-constructs.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
