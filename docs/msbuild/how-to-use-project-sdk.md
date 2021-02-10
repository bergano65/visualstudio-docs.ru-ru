---
title: Практическое руководство. Ссылка на пакет SDK проекта MSBuild | Документация Майкрософт
description: Узнайте, как использование пакетов SDK проекта MSBuild упрощает применение пакетов разработки программного обеспечения, требующих импортировать свойства и целевые объекты.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914217"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Информация об использовании пакетов SDK проекта MSBuild

MSBuild 15.0 представляет новую концепцию "пакет SDK проекта", которая упрощает применение пакетов разработки программного обеспечения, требующих импортировать свойства и целевые объекты.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

На этапе оценки проекта MSBuild добавляет неявные директивы импорта в начале и конце файла проекта:

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

- Используйте атрибут `Sdk` в элементе `<Project/>`.

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    При этом в начале и конце кода проекта добавляются неявные директивы импорта, как описано выше.
    
    Чтобы указать определенную версию пакета SDK, добавьте ее в атрибут `Sdk`:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Используйте элемент `<Sdk/>` верхнего уровня.

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   При этом в начале и конце кода проекта добавляются неявные директивы импорта, как описано выше.
   
   Атрибут `Version` не является обязательным.

- Используйте элемент `<Import/>` в любом месте кода проекта.

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

   Если вы используете элемент `<Import/>`, можно указать необязательный атрибут `Version`. Например, так: `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Как разрешаются ссылки на пакеты SDK проекта

При оценке директив импорта MSBuild динамически разрешает путь к пакету SDK проекта, используя указанные значения имени и версии.  Также MSBuild использует список зарегистрированных сопоставителей SDK. Это подключаемые модули, которые отвечают за расположение пакетов SDK на компьютере. Далее следует список этих подключаемых модулей.

- Распознаватель на основе NuGet, который опрашивает настроенные каналы пакетов в поисках пакетов NuGet с указанными значениями идентификатора и версии пакета SDK.

   Этот сопоставитель применяется только в том случае, если вы указали необязательное значение версии. Его можно использовать для любых пользовательских пакетов SDK проекта.
   
- Сопоставитель пакетов SDK для .NET, который разрешает пакеты SDK для MSBuild, установленные совместно с [пакетом SDK для .NET](/dotnet/core/sdk/).

   Этот сопоставитель находит только пакеты SDK проекта, входящие в состав этого продукта, например `Microsoft.NET.Sdk` и `Microsoft.NET.Sdk.Web`.
   
- Распознаватель по умолчанию, который разрешает пакеты SDK, установленные совместно с MSBuild.

Сопоставитель пакетов SDK на основе NuGet позволяет указывать версию в файле [global.json](/dotnet/core/tools/global-json), благодаря чему вы можете управлять версией пакета SDK проекта в одном месте, а не в каждом проекте отдельно:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

При сборке проекта может использоваться только одна версия каждого пакета SDK проекта. Если указать ссылки на две разные версии одного пакета SDK проекта, MSBuild выдает предупреждение. Рекомендуем **не** указывать в проектах версию, если она уже указана в файле *global.json*.

## <a name="see-also"></a>См. также раздел

- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [Настройка сборки](../msbuild/customize-your-build.md)
- [Пакеты, метаданные и платформы](/dotnet/core/packages)
- [Дополнения к формату CSPROJ для .NET Core](/dotnet/core/tools/csproj)
