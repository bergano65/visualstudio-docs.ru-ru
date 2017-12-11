---
title: "Настройка системы сборки | Документы Майкрософт"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 2d17a952c58e5ef7e593ee7aeb1980e09a376800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-build-system"></a>Настройка системы сборки

MSbuild — это подсистема сборки, разработанная корпорацией Майкрософт и ориентированная на разработку приложений .NET. Платформа Mono также имеет собственную реализацию Microsoft Build Engine, которая называется **xbuild**. Однако использование xbuild было постепенно прекращено, и вместо нее во всех операционных системах стала применяться MSBuild.

**MSbuild** в основном используется в качестве системы сборки для проектов в Visual Studio для Mac. 

MSBuild принимает набор входных данных, таких как файлы исходного кода, и преобразует их в выходные данные, такие как исполняемые файлы, используя для этого такие средства, как компилятор. 


## <a name="msbuild-file"></a>Файл MSBuild

MSBuild использует XML-файл, называемый файлом проекта, который определяет *элементы*, входящие в состав проекта (например, ресурсы изображений), и *свойства*, необходимые для сборки проекта. Расширение этого файла всегда заканчивается на `proj`, например `.csproj` для проектов C#. 

### <a name="viewing-the-msbuild-file"></a>Просмотр файла MSBuild
Этот файл можно найти, щелкнув правой кнопкой мыши имя проекта и выбрав пункт **Отобразить в Finder**. При этом отображаются все файлы и папки, относящиеся к проекту, включая файл `.csproj`, как показано ниже:

![](media/customizing-build-system-image1.png)

Можно также отобразить `.csproj` на новой вкладке в Visual Studio для Mac, щелкнув правой кнопкой мыши имя проекта и выбрав **Сервис > Изменить файл**:

![](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Композиция файла MSBuild

Все файлы MSBuild содержат обязательный корневой элемент `Project`, как показано ниже:

```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Как правило, проект также импортирует файл `.targets`, который содержит множество правил, описывающих обработку и сборку различных файлов. Обычно они расположены ближе к концу файла `proj`, и для проектов C# будут выглядеть примерно следующим образом:

```
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Файл целей построения — еще один файл MSBuild. Он содержит код MSBuild, который может использоваться в нескольких проектах. Например, файл `Microsoft.CSharp.targets`, который находится в каталоге, представленным свойством `MSBuildBinPath` (или переменной), содержит логику для создания сборок C# из исходных файлов C#.

### <a name="items-and-properties"></a>Элементы и свойства

В MSBuild существует два основных типа данных: *элементы* и *свойства*, которые подробнее описаны ниже.

#### <a name="properties"></a>Свойства

Свойства — это пары "ключ-значение", которые используются для хранения параметров, влияющих на компиляцию, например, параметров компилятора.

Они задаются с помощью PropertyGroup и могут содержать любое количество PropertiesGroup, где может находиться любое количество свойств. 

Например, PropertyGroup для простого консольного приложения может выглядеть следующим образом:

```
<PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
        <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>refactoring</RootNamespace>
        <AssemblyName>refactoring</AssemblyName>
        <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
    </PropertyGroup>
```

На свойства можно ссылаться из выражений с помощью синтаксиса `$()`. Например, `$(Foo)` будет интерпретироваться как значение свойства `Foo`. Если это свойство не задано, оно интерпретируется как пустая строка без возникновения ошибки.

#### <a name="items"></a>Элементы

Элементы позволяют работать с входными данными системы сборки, такими как списки и наборы, и обычно представляют файлы. Каждый элемент имеет *тип*, *спецификацию* и необязательные произвольные *метаданные*. Обратите внимание, что MSBuild не работает с отдельными элементами, а получает все элементы заданного типа в виде *набора* элементов.

Элементы создаются путем объявления `ItemGroup`. Может существовать любое количество ItemGroup, способных содержать любое число элементов. 

Например, приведенный ниже фрагмент кода создает экраны запуска iOS. Они имеют тип `BundleResource` со спецификацией в виде пути к изображению:

```
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```
 
 На наборы элементов можно ссылаться из выражений с помощью синтаксиса `@()`. Например, `@(BundleResource)` будет интерпретироваться как набор элементов BundleResource, включающий в себя все элементы BundleResource. Если элементы этого типа отсутствуют, он будет интерпретироваться как пустой без возникновения ошибки.

## <a name="resources-for-learning-msbuild"></a>Ресурсы для изучения MSBuild

Дополнительные сведения о MSBuild см. в следующих ресурсах:

* [Обзор на сайте MSDN](https://msdn.microsoft.com/library/dd393574.aspx)
* [Основные понятия на сайте MSDN](https://msdn.microsoft.com/library/dd637714.aspx)


