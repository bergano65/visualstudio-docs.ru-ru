---
title: Практическое руководство. Ссылка на пакет SDK проекта MSBuild | Документация Майкрософт
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abc61f0e07ed1e22d0ec3b2c8fb15d66c9eea3cd
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220453"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Информация об использовании пакетов SDK проекта MSBuild

В версии [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 представлена новая концепция "пакет SDK проекта", которая упрощает применение пакетов разработки программного обеспечения, требующих импортировать свойства и целевые объекты.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

На этапе оценки проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] добавляет неявные директивы импорта в начале и конце кода проекта:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Ссылка на пакет SDK проекта

 Есть три разных способа указать ссылку на пакет SDK проекта:

1. Используйте атрибут `Sdk` в элементе `<Project/>`.

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    При этом в начале и конце кода проекта добавляются неявные директивы импорта, как описано выше.  Значение атрибута `Sdk` задается в формате `Name[/Version]`, где Version обозначает необязательное значение версии.  Например, так: `My.Custom.Sdk/1.2.3`.

    > [!NOTE]
    > Сейчас это единственный способ добавить ссылку на пакет SDK для проекта в Visual Studio для Mac.

2. Используйте элемент `<Sdk/>` верхнего уровня.

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   При этом в начале и конце кода проекта добавляются неявные директивы импорта, как описано выше.  Атрибут `Version` не является обязательным.

3. Используйте элемент `<Import/>` в любом месте кода проекта.

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   Явное включение директив импорта позволяет самостоятельно контролировать порядок добавления элементов.

   Если вы используете элемент `<Import/>`, можно указать необязательный атрибут `Version`.  Например, так: `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Как разрешаются ссылки на пакеты SDK проекта

При оценке директив импорта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] динамически разрешает путь к пакету SDK проекта, используя указанные значения имени и версии.  Также [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] использует список зарегистрированных распознавателей SDK. Это подключаемые модули, которые отвечают за расположение пакетов SDK на компьютере.  Далее следует список этих подключаемых модулей.

1. Распознаватель на основе NuGet, который опрашивает настроенные каналы пакетов в поисках пакетов NuGet с указанными значениями идентификатора и версии пакета SDK.<br/>
   Этот распознаватель применяется только в том случае, если вы указали необязательное значение версии. Его можно использоваться для любых пользовательских пакетов SDK проекта.  
2. Распознаватель .NET CLI, который разрешает пакеты SDK, установленные совместно с .NET CLI.<br/>
   Этот распознаватель находит только пакеты SDK проекта, входящие в состав этого продукта, например `Microsoft.NET.Sdk` и `Microsoft.NET.Sdk.Web`.
3. Распознаватель по умолчанию, который разрешает пакеты SDK, установленные совместно с MSBuild.

Распознаватель пакетов SDK на основе NuGet позволяет указывать версию в файле [global.json](https://docs.microsoft.com/dotnet/core/tools/global-json), благодаря чему вы можете управлять версией пакета SDK проекта в одном месте, а не в каждом проекте отдельно.

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

При сборке проекта может использоваться только одна версия каждого пакета SDK проекта.  Если вы укажете ссылки на две разные версии одного пакета SDK проекта, MSBuild выдаст следующее предупреждение.  Рекомендуем **не** указывать в проектах версию, если она уже указана в файле *global.json*.  

## <a name="see-also"></a>См. также

 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Настройка сборки](../msbuild/customize-your-build.md)   
 [Пакеты, метаданные и платформы](/dotnet/core/packages)   
 [Дополнения к формату CSPROJ для .NET Core](/dotnet/core/tools/csproj)
