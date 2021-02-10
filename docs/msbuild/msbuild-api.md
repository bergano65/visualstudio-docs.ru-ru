---
title: API MSBuild | Документы Майкрософт
description: Сведения об общедоступном интерфейсе API в MSBuild, который позволяет программам выполнять сборку и проверять проекты.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b376f1cb1d6b473c0ea37bb33f6ae2b60789fa24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919302"
---
# <a name="use-the-msbuild-api"></a>Использование API MSBuild

MSBuild предоставляет общедоступный интерфейс API, который позволяет программам выполнять сборку и проверять проекты. Последние версии API MSBuild можно найти в следующих пакетах NuGet:

| Имя пакета | Описание |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Содержит сборку Microsoft.Build, которая используется для создания, изменения и вычисления проектов MSBuild.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Содержит общую сборку платформы MSBuild, используемую другими сборками MSBuild. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Предоставляет полную исполняемую копию MSBuild. Ссылаться на этот пакет следует только в том случае, если приложению требуется загружать проекты или выполнять внутрипроцессные сборки без установки MSBuild. Для успешного вычисления проектов, использующих этот пакет, необходимо выполнить статистическую обработку дополнительных компонентов (например, компиляторов) в каталоге приложения. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Содержит сборку Microsoft.Build.Tasks, которая реализует часто используемые задачи MSBuild. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Содержит сборку Microsoft.Build.Utilities, которая используется для реализации пользовательских задач MSBuild. |

Кроме того, NuGet также содержит устаревшую сборку [Microsoft.Build.Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), использовать которую не рекомендуется.

Существует несколько различных версий API MSBuild, а для версий 15 и 16 существует две различные формы сборок в пакетах NuGet, одна из которых компилируется с .NET Framework, а другая — с .NET Core, который является подмножеством API .NET Framework.  Версия .NET Core MSBuild используется при вызове команды `dotnet` и при использовании MSBuild в системах Mac и Linux.

Документацию по API MSBuild можно найти с помощью [Браузера .NET API](/dotnet/api) или в списке пространств имен, приведенных ниже.

::: moniker range="vs-2017"
| Пространство имен | Применение | Описание |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Все |  Содержит типы, используемые объектной моделью MSBuild для создания корней проекта с невычисленными значениями. Каждый корень проекта соответствует файлу проекта или файлу целей построения. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Все | Содержит класс `ProjectOptions`, поддерживающий создание проекта. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Все | Содержит типы, используемые объектной моделью MSBuild для вычисления проектов. Каждый проект связан с одним или несколькими корнями проекта. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Все | Содержит класс `EvaluationContext`, используемый для хранения состояния вычисления во всех вызовах. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Все | Содержит типы исключений, которые могут выдаваться в процессе сборки. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Все | Содержит типы, используемые объектной моделью MSBuild для создания проектов. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Все | Содержит типы, определяющие, каким образом задачи и средства ведения журнала взаимодействуют с обработчиком MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Все | Содержит типы, поддерживающие профилирование производительности. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | Только .NET Framework | Содержит классы, используемые для представления типов XAML, полученных в результате анализа файлов, правил и других источников. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Все | Содержит классы, поддерживающие обработку подстановочных знаков. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Все | Содержит типы, поддерживающие расширения для обработки подстановочных знаков. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Все | Содержит типы, поддерживающие параметр `-graph` MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Все | Содержит типы, используемые для регистрации хода выполнения сборки. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Все | Содержит типы, поддерживающие удаленное взаимодействие в MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Все | Содержит реализацию всех задач, поставляемых с MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | Только .NET Framework | Содержит классы, используемые внутри MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | Только .NET Framework | Содержит классы, используемые MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Все | Содержит классы, используемые внутри MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | Только .NET Framework | Содержит классы, связанные с задачами сборки XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Все | Содержит вспомогательные классы, которые можно использовать для создания собственных средств ведения журнала и задач MSBuild.|
:::moniker-end
:::moniker range=">=vs-2019"
| Пространство имен | Применение | Описание |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Все |  Содержит типы, используемые объектной моделью MSBuild для создания корней проекта с невычисленными значениями. Каждый корень проекта соответствует файлу проекта или файлу целей построения. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Все | Содержит класс `ProjectOptions`, поддерживающий создание проекта. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Все | Содержит типы, используемые объектной моделью MSBuild для вычисления проектов. Каждый проект связан с одним или несколькими корнями проекта. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Все | Содержит класс `EvaluationContext`, используемый для хранения состояния вычисления во всех вызовах. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Все | Содержит типы исключений, которые могут выдаваться в процессе сборки. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Все | Содержит типы, используемые объектной моделью MSBuild для создания проектов. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Все | Содержит типы, определяющие, каким образом задачи и средства ведения журнала взаимодействуют с обработчиком MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Все | Содержит типы, поддерживающие профилирование производительности. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | Только .NET Framework | Содержит классы, используемые для представления типов XAML, полученных в результате анализа файлов, правил и других источников. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Все | Содержит классы, поддерживающие обработку подстановочных знаков. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Все | Содержит типы, поддерживающие расширения для обработки подстановочных знаков. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Все | Содержит типы, поддерживающие параметр `-graph` MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Все | Содержит типы, используемые для регистрации хода выполнения сборки. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Все | Содержит типы, поддерживающие удаленное взаимодействие в MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Все | Содержит реализацию всех задач, поставляемых с MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | Только .NET Framework | Содержит классы, используемые внутри MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | Только .NET Framework | Содержит классы, используемые MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Все | Содержит классы, используемые внутри MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | Только .NET Framework | Содержит классы, связанные с задачами сборки XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Все | Содержит вспомогательные классы, которые можно использовать для создания собственных средств ведения журнала и задач MSBuild.|
:::moniker-end

В приведенной выше таблице "Все" в столбце "Применение" означает, что типы в пространстве имен доступны как в .NET Framework, так и в версиях .NET Core для API MSBuild.
