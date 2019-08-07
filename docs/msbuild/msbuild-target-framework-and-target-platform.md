---
title: 'MSBuild: целевая рабочая среда и целевая платформа | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00874c8fd7ded67c380de1166d7e9753a3bd3c24
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68662041"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild: целевая рабочая среда и целевая платформа
Проект может быть создан для выполнения в *требуемой версии .NET Framework*, которая является конкретной версией платформы .NET Framework, и на *целевой платформе*, которая является конкретной программной архитектурой.  Например, можно настроить приложение для выполнения в .NET Framework 2.0 на 32-разрядной платформе, которая совместима с семейством процессоров 802x86 ("x86"). Сочетание требуемой версии .NET Framework и целевой платформы называется *целевым контекстом*.

> [!IMPORTANT]
> В этой статье показан старый способ указания целевой платформы. Проекты в стиле пакетов SDK позволяют использовать разные TargetFrameworks, такие как netstandard. Дополнительные сведения см. в разделе [Требуемые версии .NET Framework](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Целевая платформа и профиль
 Целевая платформа — это конкретная версия .NET Framework, для выполнения на которой создан проект. Спецификация целевой платформы является необходимым условием, поскольку она позволяет использовать возможности компилятора и ссылки на сборки, предназначенные исключительно для этой версии платформы.

 В настоящее время доступны следующие версии платформы .NET Framework.

- .NET Framework 2.0 (входит в состав Visual Studio 2005)

- .NET Framework 3.0 (входит в состав [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])

- .NET Framework 3.5 (входит в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])

- .NET Framework 4.5.2

- .NET Framework 4.6 (входит в состав [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Версии платформы .NET Framework отличаются друг от друга в списке сборок, доступном для использования в справочных целях. Например, приложения WPF можно создавать, только если проект предназначен для платформы .NET Framework версии 3.0 или выше.

Целевая версия .NET Framework указывается в свойстве `TargetFrameworkVersion` в файле проекта. Целевую версию .NET Framework для проекта можно изменить с помощью страниц свойств проекта в интегрированной среде разработки Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. определить целевую версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Доступными значениями для `TargetFrameworkVersion` являются `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` и `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Целевой профиль* — это подмножество целевой платформы. Например, профиль клиента .NET Framework 4 не содержит ссылок на сборки MSBuild.

 Целевой профиль указывается в свойстве `TargetFrameworkProfile` в файле проекта. Целевой профиль можно изменить с помощью элемента управления целевой платформы на страницах свойств проекта в интегрированной среде разработки. Дополнительные сведения см. в разделе [Практическое руководство. определить целевую версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Целевая платформа
 *Платформа* — это сочетание оборудования и программного обеспечения, которое определяет конкретную среду выполнения. Например, примененная к объекту директива

- `x86` обозначает 32-разрядную операционную систему Windows, работающую с процессором Intel 80x86 или эквивалентным.

- `x64` обозначает 64-разрядную операционную систему Windows, работающую с процессором Intel x64 или эквивалентным.

- `Xbox` обозначает платформу Microsoft Xbox 360.

*Целевая платформа* — это конкретная платформа, для выполнения на которой создан проект. Целевая платформа указывается в свойстве сборки `PlatformTarget` в файле проекта. Целевую платформу можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций** в интегрированной среде разработки.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Целевая конфигурация* — это подмножество целевой платформы. Например, конфигурация `x86``Debug` не поддерживает большинство видов оптимизации кода. Целевая конфигурация указывается в свойстве сборки `Configuration` в файле проекта. Целевую конфигурацию можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>См. также
- [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
