---
title: Настройка системы сборки
description: В этой статье кратко описывается система сборки MSBuild, используемая в Visual Studio для Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128391"
---
# <a name="customizing-the-build-system"></a>Настройка системы сборки

Microsoft Build Engine представляет собой платформу для сборки приложений. Эта платформа, которая также называется MSBuild, была разработана корпорацией Майкрософт и ориентирована на разработку приложений .NET. Платформа Mono также имеет собственную реализацию Microsoft Build Engine, которая называется **xbuild**. Однако к текущему времени использование xbuild было постепенно прекращено, и вместо нее во всех операционных системах стала применяться платформа MSBuild.

**MSBuild** используется в качестве системы сборки для проектов в Visual Studio для Mac, принимая набор входных данных, таких как файлы исходного кода, и преобразовывая их в выходные данные, такие как исполняемые файлы. Для этого используются такие средства, как компилятор.

## <a name="msbuild-file"></a>Файл MSBuild

MSBuild использует XML-файл, называемый файлом проекта, который определяет *элементы*, входящие в состав проекта (например, ресурсы изображений), и *свойства*, необходимые для сборки проекта. Расширение этого файла всегда заканчивается на `proj`, например `.csproj` для проектов C#.

### <a name="viewing-the-msbuild-file"></a>Просмотр файла MSBuild

Чтобы найти файл MSBuild, щелкните правой кнопкой мыши имя проекта и выберите пункт **Отобразить в средстве поиска**. В окне средства поиска отобразятся все файлы и папки, относящиеся к проекту, включая файл `.csproj`, как показано на следующем изображении:

![Расположение CSPROJ в Finder](media/customizing-build-system-image1.png)

Чтобы отобразить `.csproj` на новой вкладке в Visual Studio для Mac, щелкните правой кнопкой мыши имя проекта и выберите **Сервис > Изменить файл**:

![Открытие CSPROJ в редакторе исходного кода](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Композиция файла MSBuild

Все файлы MSBuild содержат обязательный корневой элемент `Project`, например такой:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Как правило, проект также импортирует файл `.targets`. Этот файл содержит множество правил, описывающих обработку и сборку различных файлов. Обычно объект импорта расположен ближе к концу файла `proj` и для проектов C# выглядит примерно так:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Файл целей построения — еще один файл MSBuild. Он содержит код MSBuild, который может использоваться в нескольких проектах. Например, файл `Microsoft.CSharp.targets`, который находится в каталоге, представленным свойством `MSBuildBinPath` (или переменной), содержит логику для создания сборок C# из исходных файлов C#.

### <a name="items-and-properties"></a>Элементы и свойства

В MSBuild есть два основных типа данных: *элементы* и *свойства*, которые подробнее описаны в следующих разделах.

#### <a name="properties"></a>Свойства

Свойства — это пары "ключ-значение", которые используются для хранения параметров, влияющих на компиляцию, например, параметров компилятора.

Они задаются с помощью PropertyGroup и могут содержать любое число групп PropertiesGroup с любым числом свойств.

Например, PropertyGroup для простого консольного приложения может выглядеть как следующий XML-код:

```xml
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

Например, приведенный ниже фрагмент кода создает экраны запуска iOS. Экраны запуска имеют тип сборки `BundleResource` со спецификацией в виде пути к изображению:

```xml
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

* [MSBuild Overview](/visualstudio/msbuild/msbuild) (Общие сведения о MSBuild)
* [Основные понятия MSBuild](/visualstudio/msbuild/msbuild-concepts)
