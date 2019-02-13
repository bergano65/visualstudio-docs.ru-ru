---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools 2017
titleSuffix: ''
description: Идентификаторы рабочих нагрузок и компонентов Visual Studio можно использовать для создания классических приложений Windows
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: ad043d82dcefd899bbffd4d931506732c474f2f5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948437"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Каталог компонентов для Visual Studio Build Tools 2017

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки или в качестве зависимости в манифесте VSIX. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты.
* По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Когда вы включаете зависимости в манифест VSIX, достаточно указать только идентификаторы компонентов. Таблицы на этой странице позволяют определить минимальный набор зависимостей компонентов. В некоторых сценариях нужно указать лишь один компонент из рабочей нагрузки. В других случаях потребуется несколько компонентов из одной рабочей нагрузки или несколько компонентов из нескольких рабочих нагрузок. Дополнительные сведения см. в разделе [Практическое руководство. Перенос проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="azure-development-build-tools"></a>Средства сборки и разработки Azure

**Идентификатор:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Описание.** Задачи и целевые объекты MSBuild для сборки приложений Azure.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 15.7.27617.1 | Обязательно
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательно
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Средства сборки для разработки WCF | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Средства сборки для веб-разработчиков | 15.8.27729.1 | Обязательно
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Optional

## <a name="data-storage-and-processing-build-tools"></a>Средства сборки для хранения и обработки данных

**Идентификатор:** Microsoft.VisualStudio.Workload.DataBuildTools

**Описание.** Сборка проектов базы данных SQL Server

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools — средства сборки | 15.8.27825.0 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное

## <a name="net-desktop-build-tools"></a>Средства сборки классических приложений .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Описание.** Средства создания приложений на основе WPF, Windows Forms и консольных приложений с помощью C#, Visual Basic и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Microsoft.Component.ClickOnce.MSBuild | Средства сборки ClickOnce | 15.7.27617.1 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.TestTools.BuildTools | Основные компоненты инструментов тестирования — средства сборки | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Средства сборки для разработки WCF | 15.6.27309.0 | Рекомендованное
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# - компилятор | 15.8.27825.0 | Optional

## <a name="msbuild-tools"></a>MSBuild Tools

**Идентификатор:** Microsoft.VisualStudio.Workload.MSBuildTools

**Описание.** Средства, необходимые для сборки приложений на основе MSBuild.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.VisualStudio.Component.CoreBuildTools | Ядро Visual Studio Build Tools | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно

## <a name="net-core-build-tools"></a>Средства сборки .NET Core

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Описание.** Средства сборки приложений с помощью .NET Core, ASP.NET Core, HTML/JavaScript и контейнеров.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Обязательно
Microsoft.NetCore.BuildTools.ComponentGroup | Средства сборки .NET Core | 15.8.27906.1 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Средства сборки Node.js

**Идентификатор:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Описание.** Задачи и целевые объекты MSBuild для создания масштабируемых сетевых приложений, использующих Node.js, асинхронную среду выполнения JavaScript, управляемую событиями.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Поддержка MSBuild в Node.js | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательно

## <a name="officesharepoint-build-tools"></a>Средства сборки Office и SharePoint

**Идентификатор:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Описание.** Создание надстроек Office, SharePoint и VSTO.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Средства сборки ClickOnce | 15.7.27617.1 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Средства сборки и разработки Office и SharePoint | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.Workflow.BuildTools | Средства сборки Windows Workflow Foundation | 15.8.27906.1 | Обязательно
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Средства сборки для разработки WCF | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Средства сборки для веб-разработчиков | 15.8.27729.1 | Обязательно
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Средства сборки набора средств Visual Studio для Office (VSTO) | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Optional

## <a name="universal-windows-platform-build-tools"></a>Инструменты для создания приложений универсальной платформы Windows

**Идентификатор:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Описание.** Предоставляет инструменты, необходимые для создания приложений универсальной платформы Windows.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Обязательно
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Обязательно
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Необходимые компоненты для создания приложений универсальной платформы Windows | 15.8.27705.0 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Пакет SDK для Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**Идентификатор:** Microsoft.VisualStudio.Workload.VCTools

**Описание.** Создание классических приложений Windows с помощью набора инструментов Microsoft C++, ATL или MFC.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Основные возможности Visual C++ Build Tools | 15.8.27729.1 | Обязательно
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Распространяемый компонент Visual C++ 2017 с обновлением | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.TestTools.BuildTools | Основные компоненты инструментов тестирования — средства сборки | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Инструменты Visual C++ для CMake | 15.8.27906.1 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.8.27924.0 | Рекомендованное
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 v14.00 (v140) для ПК | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL для x86 и x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC для x86 и x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули для стандартной библиотеки (экспериментальная версия) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Компиляторы и библиотеки Visual C++ для ARM64 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Поддержка Windows XP для C++ | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Поддержка Windows XP для C++ | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Пакет SDK для Windows 10 (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-studio-extension-development"></a>Разработка расширений Visual Studio

**Идентификатор:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**Описание.** Средства для создания надстроек и расширений для Visual Studio, включая новые команды, средства анализа кода и окна инструментов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.VSSDKBuildTools | Основные компоненты Visual Studio Build Tools | 15.8.27924.0 | Обязательно
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Необходимые компоненты для разработки расширений Visual Studio | 15.8.27729.1 | Обязательно
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL для x86 и x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC для x86 и x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Последняя версия 141 инструментов версии 14.16 для VC++ 2017 версии 15.9 | 15.9.28230.55 | Optional

## <a name="web-development-build-tools"></a>Средства сборки для веб-разработчиков

**Идентификатор:** Microsoft.VisualStudio.Workload.WebBuildTools

**Описание.** Задачи и целевые объекты MSBuild для сборки веб-приложений.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.1 | Пакет SDK для TypeScript 3.1 | 15.0.28218.60 | Обязательно
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Средства сборки для веб-разработчиков | 15.8.27729.1 | Обязательно
Microsoft.Component.ClickOnce.MSBuild | Средства сборки ClickOnce | 15.7.27617.1 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 15.8.27924.0 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Средства разработки для контейнеров — средства сборки | 15.7.27617.1 | Рекомендованное
Microsoft.VisualStudio.Component.TestTools.BuildTools | Основные компоненты инструментов тестирования — средства сборки | 15.7.27625.0 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Рекомендованное
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Средства сборки для разработки WCF | 15.6.27309.0 | Рекомендованное
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Средства разработки для .NET Framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 | 15.6.27406.0 | Optional

## <a name="mobile-development-with-net"></a>Разработка мобильных приложений на платформе .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Описание.** Средства создания кроссплатформенных приложений для iOS, Android и Windows на C# и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Component.Android.SDK25 | Программа установки пакета SDK для Android (уровень API 25) | 15.9.28107.0 | Optional
Component.OpenJDK | Дистрибутив OpenJDK от Майкрософт | 15.9.28125.51 | Optional

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Версия
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | Пакет SDK для TypeScript 2.0 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | Пакет SDK для TypeScript 2.2 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | Пакет SDK для TypeScript 2.3 | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | Пакет SDK для TypeScript 2.5 | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | Пакет SDK для TypeScript 2.6 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | Пакет SDK для TypeScript 2.7 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | Пакет SDK для TypeScript 2.8 | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | Пакет SDK для TypeScript 2.9 | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | Пакет SDK для TypeScript 3.0 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL для ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL для ARM с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL для ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL для ARM64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86 или x64) с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC для x86 или x64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (экспериментальная версия) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC для ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC для ARM с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC для ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Поддержка Visual C++ MFC для ARM64 с устранением рисков Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Библиотеки версии 14.16 для VC++ 2017 версии 15.9 для Spectre (x86 и x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Набор инструментов v14.11 для VC++ 2017 версии 15.4 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Набор инструментов версии 14.12 для VC++ 2017 версии 15.5 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Набор инструментов версии 14.13 для VC++ 2017 версии 15.6 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Набор инструментов версии 14.14 для VC++ 2017 версии 15.7 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Набор инструментов версии 14.15 для VC++ 2017 версии 15.8 | 15.0.28230.55

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Build Tools для Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
