---
title: Обновление существующего приложения до MSBuild 15 | Документация Майкрософт
description: Узнайте, как обеспечить соответствие между сборками, выполняемыми программными средствами из приложения, и сборками, выполняемыми в Visual Studio или с помощью MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd7f47466074536c9088840e726f768f62f9346b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965932"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Обновление существующего приложения для использования MSBuild 15

До версии 15.0 платформа MSBuild загружалась из глобального кэша сборок, а расширения MSBuild устанавливались в реестре. Благодаря этому все приложения использовали одну и ту же версию MSBuild и имели доступ к одним и тем же наборам инструментов, однако это делало невозможной параллельную установку разных версий Visual Studio.

Чтобы сделать установку более быстрой, меньшей по размеру и обеспечить ее параллельное выполнение, Visual Studio 2017 и более поздних версий больше не помещает платформу MSBuild в глобальный кэш сборок и не изменяет реестр. Недостатком является то, что приложения, которым необходимо использовать API MSBuild для анализа или сборки проектов, не могут неявно использовать установку Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Использование MSBuild из Visual Studio

Чтобы обеспечить соответствие сборок, выполняемых программными средствами из приложения, сборкам, выполняемым в Visual Studio или *MSBuild.exe*, следует загружать сборки MSBuild из Visual Studio и использовать пакеты SDK, доступные в Visual Studio. Пакет NuGet Microsoft.Build.Locator упрощает этот процесс.

## <a name="use-microsoftbuildlocator"></a>Использование пакета Microsoft.Build.Locator

Если вы распространяете пакет *Microsoft.Build.Locator.dll* вместе с приложением, распространять другие сборки MSBuild не требуется.

Чтобы обновить проект для использования MSBuild 15 и API локатора, необходимо внести в проект ряд изменений, которые описаны ниже. Чтобы ознакомиться с примером изменений, необходимых для обновления проекта, просмотрите [список фиксаций, внесенных в пример проекта, в репозитории MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Изменение ссылок на MSBuild

Чтобы убедиться, что платформа MSBuild загружается из центрального расположения, ее сборки не следует распространять вместе с приложением.

Изменения, которые необходимо внести в проект, чтобы избежать загрузки MSBuild из центрального расположения, зависят от того, как проект ссылается на MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Использование пакетов NuGet (предпочтительный способ)

В этих инструкциях предполагается, что вы используете [ссылки NuGet в стиле PackageReference](/nuget/consume-packages/package-references-in-project-files).

Измените файлы проекта так, чтобы они ссылались на сборки MSBuild из пакетов NuGet. Задайте тег `ExcludeAssets=runtime`, чтобы сообщить диспетчеру NuGet, что сборки требуются только во время сборки и их не следует копировать в выходной каталог.

Основной и дополнительные номера версии пакетов MSBuild должны быть не выше минимальной версии Visual Studio, которая должна поддерживаться. Например, если вы хотите обеспечить поддержку Visual Studio 2017 и более поздних версий, укажите версию пакета `15.1.548`.

Например, можно использовать следующий код XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Использование сборок расширений

Если использовать пакеты NuGet невозможно, можно ссылаться на сборки MSBuild, распространяемые вместе с Visual Studio. При прямой ссылке на платформу MSBuild она не должна копироваться в выходной каталог. Для этого следует присвоить свойству `Copy Local` значение `False`. В файле проекта этот параметр будет выглядеть следующим образом:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Переадресации привязок

При ссылке на пакет Microsoft.Build.Locator необходимо убедиться, что приложение автоматически использует необходимые перенаправления привязок на версию 15.1.0.0. Для перенаправления привязок на эту версию поддерживается как MSBuild 15, так и MSBuild 16.

### <a name="ensure-output-is-clean"></a>Очистка выходных данных

Выполните сборку проекта и проверьте выходной каталог, чтобы убедиться в том, что в нем нет сборок *Microsoft.Build.\*.dll*, кроме сборки *Microsoft.Build.Locator.dll*, которая будет добавлена в следующем шаге.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Добавление ссылки на пакет Microsoft.Build.Locator

Добавьте ссылку на пакет NuGet [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Не указывайте `ExcludeAssets=runtime` для пакета Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Регистрация экземпляра перед вызовом MSBuild

> [!IMPORTANT]
> В методе, который вызывает MSBuildLocator, нельзя использовать типы MSBuild (из пространства имен `Microsoft.Build`). Например, нельзя выполнить следующее.
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> Вместо этого необходимо поступить так.
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

Самый простой способ добавить вызов к API Locator — это добавить вызов

```csharp
MSBuildLocator.RegisterDefaults();
```

в коде запуска приложения.

Чтобы более детально контролировать загрузку MSBuild, можно вручную выбрать результат `MSBuildLocator.QueryVisualStudioInstances()` для передачи в метод `MSBuildLocator.RegisterInstance()`, но, как правило, делать этого не требуется.
