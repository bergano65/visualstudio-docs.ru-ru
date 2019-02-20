---
title: Обновление существующего приложения до MSBuild 15 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9db632ba38d408223928d43921da8dd188fe93d9
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227255"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Обновление существующего приложения для использования MSBuild 15

До версии 15.0 платформа MSBuild загружалась из глобального кэша сборок, а расширения MSBuild устанавливались в реестре. Благодаря этому все приложения использовали одну и ту же версию MSBuild и имели доступ к одним и тем же наборам инструментов, однако это делало невозможной параллельную установку разных версий Visual Studio.

Для более быстрой, меньшей по размеру, а также параллельной установки в Visual Studio 2017 платформа MSBuild больше не помещается в глобальный кэш сборок и реестр не изменяется. Недостатком является то, что приложения, которым необходимо использовать API MSBuild для анализа или сборки проектов, не могут неявно использовать установку Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Использование MSBuild из Visual Studio

Чтобы обеспечить соответствие сборок, выполняемых программными средствами из приложения, сборкам, выполняемым в Visual Studio или *MSBuild.exe*, следует загружать сборки MSBuild из Visual Studio и использовать пакеты SDK, доступные в Visual Studio. Пакет NuGet Microsoft.Build.Locator упрощает этот процесс.

## <a name="use-microsoftbuildlocator"></a>Использование пакета Microsoft.Build.Locator

Если вы распространяете пакет *Microsoft.Build.Locator.dll* вместе с приложением, распространять другие сборки MSBuild не требуется.

Чтобы обновить проект для использования MSBuild 15 и API локатора, необходимо внести в проект ряд изменений, которые описаны ниже. Чтобы ознакомиться с примером изменений, необходимых для обновления проекта, просмотрите [список фиксаций, внесенных в пример проекта, в репозитории MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Изменение ссылок на MSBuild

Чтобы убедиться, что платформа MSBuild загружается из центрального расположения, ее сборки не следует распространять вместе с приложением.

Изменения, которые необходимо внести в проект, чтобы избежать загрузки MSBuild из центрального расположения, зависят от того, как проект ссылается на MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Использование пакетов NuGet (предпочтительный способ)

В этих инструкциях предполагается, что вы используете [ссылки NuGet в стиле PackageReference](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

Измените файлы проекта так, чтобы они ссылались на сборки MSBuild из пакетов NuGet. Задайте тег `ExcludeAssets=runtime`, чтобы сообщить диспетчеру NuGet, что сборки требуются только во время сборки и их не следует копировать в выходной каталог.

Основной и дополнительные номера версии пакетов MSBuild должны быть не выше минимальной версии Visual Studio, которая должна поддерживаться. Чтобы поддерживалась любая версия Visual Studio 2017, следует ссылаться на версию пакетов `15.1.548`.

Например, можно использовать следующий код XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
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

При ссылке на пакет Microsoft.Build.Locator необходимо убедиться, что приложение автоматически использует необходимые переадресации привязок со всех версий сборок MSBuild на версию `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Очистка выходных данных

Выполните сборку проекта и проверьте выходной каталог, чтобы убедиться в том, что в нем нет сборок *Microsoft.Build.\*.dll*, кроме сборки *Microsoft.Build.Locator.dll*, которая будет добавлена в следующем шаге.

### <a name="add-package-reference"></a>Добавление ссылки на пакет

Добавьте ссылку на пакет NuGet [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Регистрация экземпляра перед вызовом MSBuild

Добавьте вызов API Locator перед вызовом любых методов, использующих MSBuild.

Самый простой способ добавить вызов к API Locator — это добавить вызов

```csharp
MSBuildLocator.RegisterDefaults();
```

в коде запуска приложения.

Чтобы более детально контролировать загрузку MSBuild, можно вручную выбрать результат `MSBuildLocator.QueryVisualStudioInstances()` для передачи в метод `MSBuildLocator.RegisterInstance()`, но, как правило, делать этого не требуется.
