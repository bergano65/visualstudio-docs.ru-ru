---
title:
- "Идентификаторы рабочих нагрузок и компонентов для Visual Studio Community 2017 | Документация Майкрософт"
description: "Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX."
keywords: 
author:
- TerryGLee
ms.author:
- tglee
manager:
- ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 58494fc3-12de-4761-bd4a-74b54f72bfb3
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 9055f1352cce133d853d73d378933ddf8b7e3d78
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-community-2017-workload-and-component-ids"></a>Идентификаторы рабочих нагрузок и компонентов для Visual Studio Community 2017

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки или в качестве зависимости в манифесте VSIX. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты. По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Когда вы включаете зависимости в манифест VSIX, достаточно указать только идентификаторы компонентов. Таблицы на этой странице позволяют определить минимальный набор зависимостей компонентов. В некоторых сценариях нужно указать лишь один компонент из рабочей нагрузки. В других случаях потребуется несколько компонентов из одной рабочей нагрузки или несколько компонентов из нескольких рабочих нагрузок. Дополнительные сведения см. в статье [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Руководство по переносу проектов расширения среды на Visual Studio 2017).

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).


## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Основной редактор Visual Studio (входит в состав Visual Studio Community 2017)

**Идентификатор.** Microsoft.VisualStudio.Workload.CoreEditor

**Описание.** Основные возможности оболочки Visual Studio, включая редактирование кода с учетом синтаксиса, управление исходным кодом и рабочими элементами.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Основной редактор Visual Studio | Обязательное


## <a name="azure-development"></a>Разработка для Azure

**Идентификатор.** Microsoft.VisualStudio.Workload.Azure

**Описание.** Пакет SDK Azure, средства и проекты для разработки облачных приложений и создания ресурсов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.Component.NetFX.Core.Runtime | Среда выполнения .NET Core | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0.1 | Обязательное
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 | Обязательное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | Обязательное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Обязательное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Обязательное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Необходимые компоненты для разработки на базе Azure | Обязательное
Component.WebSocket | WebSocket4Net | Рекомендованное
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake | Рекомендованное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Пакет SDK для мобильных приложений Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Основные инструменты Azure Resource Manager | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Средства Service Fabric | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Рекомендованное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Рекомендованное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Рекомендованное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Инструменты облачных служб Azure | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Средства Azure Resource Manager | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy службы хранилища Azure | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | Инструменты PowerShell | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>Хранение и обработка данных

**Идентификатор.** Microsoft.VisualStudio.Workload.Data

**Описание.** Подключение, разработка и тестирование решений по обработке данных с помощью SQL Server, Azure Data Lake, Hadoop или машинного обучения Azure.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | Рекомендованное
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | Рекомендованное
Component.Redgate.SQLSearch.VSExtension | Поиск Redgate SQL | Рекомендованное
Component.WebSocket | WebSocket4Net | Рекомендованное
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake | Рекомендованное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Рекомендованное
Microsoft.Component.MSBuild | MSBuild | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Рекомендованное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Рекомендованное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Рекомендованное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Рекомендованное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Рекомендованное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Рекомендованное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Рекомендованное
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | Optional


## <a name="net-desktop-development"></a>Разработка классических приложений .NET

**Идентификатор.** Microsoft.VisualStudio.Workload.ManagedDesktop

**Описание.** Разработка приложений WPF, Windows Forms и консольных приложений с использованием .NET Framework.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Обязательное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Обязательное
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Рекомендованное
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | Optional
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Средства разработки .NET Core 1.0–1.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | Клон кода | Optional
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | Optional
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | Optional


## <a name="game-development-with-unity"></a>Разработка игр с помощью Unity

**Идентификатор.** Microsoft.VisualStudio.Workload.ManagedGame

**Описание.** Создание двухмерных и трехмерных игр с помощью мощной кроссплатформенной среды разработки Unity.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.Unity | Набор средств Visual Studio для Unity | Обязательное
Component.UnityEngine | Редактор Unity | Рекомендованное


## <a name="linux-development-with-c"></a>Разработка приложений для Linux на C++

**Идентификатор.** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Описание.** Создание и отладка приложений, запускаемых в среде Linux.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.MDD.Linux | Visual C++ для разработки в среде Linux | Обязательное
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Обязательное
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | Обязательное


## <a name="desktop-development-with-c"></a>Разработка классических приложений на C++

**Идентификатор.** Microsoft.VisualStudio.Workload.NativeDesktop

**Описание.** Создание классических приложений для Windows с помощью набора инструментов Visual C++, библиотеки ATL и дополнительных средств, таких как MFC и C++/CLI.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | Обязательное
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Обязательное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | Обязательное
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Обязательное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Обязательное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Обязательное
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Обязательное
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Инструменты разработки архитектуры для C++ | Обязательное
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Основные возможности Visual C++ для классических приложений | Обязательное
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Инструменты Visual C++ для CMake | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Рекомендованное
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Optional
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 версии 140 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VC.ATL | Поддержка библиотеки ATL для Visual C++ | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Поддержка библиотек MFC и ATL (x86 и x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (экспериментальная версия) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули стандартных библиотек | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | Optional
Microsoft.VisualStudio.Component.WinXP | Поддержка Windows XP для C++ | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Поддержка Windows XP для C++ | Optional


## <a name="game-development-with-c"></a>Разработка игр на C++

**Идентификатор.** Microsoft.VisualStudio.Workload.NativeGame

**Описание.** Используйте все возможности C++ для создания профессиональных игр на базе DirectX, Unreal или Cocos2D.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | Обязательное
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Рекомендованное
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Рекомендованное
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Установщик Unreal Engine | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | Optional


## <a name="mobile-development-with-c"></a>Разработка мобильных приложений на C++

**Идентификатор.** Microsoft.VisualStudio.Workload.NativeMobile

**Описание.** Создание кроссплатформенных приложений на С++ для iOS, Android или Windows.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Обязательное
Component.Android.NDK.R13B | Пакет NDK для Android (R13B) | Рекомендованное
Component.Android.SDK19 | Установка пакета SDK для Android (уровни API 19 и 21) | Рекомендованное
Component.Android.SDK22 | Установка пакета SDK для Android (уровень API 22) | Рекомендованное
Component.Ant | Apache Ant (1.9.3) | Рекомендованное
Component.MDD.Android | Средства разработки на C++ для Android | Рекомендованное
Component.Android.Emulator | Эмулятор Visual Studio для Android | Optional
Component.Android.NDK.R11C | Пакет NDK для Android (R11C) | Optional
Component.Android.NDK.R11C_3264 | Пакет NDK для Android (R11C) (32-разрядная версия) | Optional
Component.Android.NDK.R12B | Пакет NDK для Android (R12B) | Optional
Component.Android.NDK.R12B_3264 | Пакет NDK для Android (R12B) (32-разрядная версия) | Optional
Component.Android.NDK.R13B_3264 | Пакет NDK для Android (R13B) (32-разрядная версия) | Optional
Component.Android.SDK23 | Установка пакета SDK для Android (уровень API 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Эмулятор Google Android (уровень API 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Пакет разработки для Java SE (8.0.920.14) | Optional
Component.MDD.IOS | Средства разработки C++ для iOS | Optional


## <a name="net-core-cross-platform-development"></a>Кроссплатформенная разработка .NET Core

**Идентификатор.** Microsoft.VisualStudio.Workload.NetCoreTools

**Описание.** Создание кроссплатформенных приложений с помощью .NET Core, ASP.NET Core, HTML, JavaScript и CSS.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.WebSocket | WebSocket4Net | Обязательное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Обязательное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0.1 | Обязательное
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 | Обязательное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Обязательное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Обязательное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Обязательное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | Обязательное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Обязательное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Обязательное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | Обязательное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Обязательное
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | Рекомендованное


## <a name="mobile-development-with-net"></a>Разработка мобильных приложений на платформе .NET

**Идентификатор.** Microsoft.VisualStudio.Workload.NetCrossPlat

**Описание.** Создание кроссплатформенных приложений для iOS, Android или Windows с помощью Xamarin.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Component.Android.NDK.R13B | Пакет NDK для Android (R13B) | Рекомендованное
Component.Android.SDK23 | Установка пакета SDK для Android (уровень API 23) | Рекомендованное
Component.Google.Android.Emulator.API23.V2 | Эмулятор Google Android (уровень API 23) | Рекомендованное
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Рекомендованное
Component.JavaJDK | Пакет разработки для Java SE (8.0.920.14) | Рекомендованное
Component.Xamarin | Xamarin | Рекомендованное
Component.Xamarin.Inspector | Xamarin Workbooks | Рекомендованное
Component.Xamarin.Profiler | Xamarin Profiler | Рекомендованное
Component.Xamarin.RemotedSimulator | Симулятор удаленной работы для Xamarin | Рекомендованное
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Рекомендованное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Рекомендованное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Optional
Microsoft.VisualStudio.Component.CodeClone | Клон кода | Optional
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Optional
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Optional
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Эмулятор Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin (2.0) | Optional


## <a name="aspnet-and-web-development"></a>ASP.NET и веб-разработка

**Идентификатор.** Microsoft.VisualStudio.Workload.NetWeb

**Описание.** Создание веб-приложений с помощью ASP.NET, ASP.NET Core, HTML, JavaScript и CSS.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.WebSocket | WebSocket4Net | Обязательное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Обязательное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0.1 | Обязательное
Microsoft.NetCore.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 | Обязательное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Обязательное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Обязательное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Обязательное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | Обязательное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Обязательное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Обязательное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | Обязательное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Обязательное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Рекомендованное
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Рекомендованное
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Рекомендованное
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | Optional
Microsoft.VisualStudio.Component.CodeClone | Клон кода | Optional
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | Optional
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | Optional
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Разработка Node.js

**Идентификатор.** Microsoft.VisualStudio.Workload.Node

**Описание.** Разработка масштабируемых сетевых приложений с помощью Node.js, асинхронной управляемой событиями среды выполнения JavaScript.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.Node.Tools | Поддержка Node.js | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Обязательное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Рекомендованное
Microsoft.VisualStudio.Component.Git | Git для Windows | Рекомендованное
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Optional


## <a name="officesharepoint-development"></a>Разработка для Office и SharePoint

**Идентификатор.** Microsoft.VisualStudio.Workload.Office

**Описание.** Создание надстроек для Office и SharePoint, решений SharePoint и надстроек для VSTO на языках C#, VB и JavaScript.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.WebSocket | WebSocket4Net | Обязательное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Обязательное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Обязательное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | Обязательное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | Обязательное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Обязательное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | Обязательное
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Sharepoint.Tools | Инструменты разработчика Office для Visual Studio | Обязательное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | Обязательное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Обязательное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Обязательное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Обязательное
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Обязательное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | Обязательное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | Обязательное
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | Обязательное
Microsoft.VisualStudio.Component.TeamOffice | Набор средств Visual Studio для Office (VSTO) | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Optional


## <a name="universal-windows-platform-development"></a>Разработка с помощью универсальной платформы Windows

**Идентификатор.** Microsoft.VisualStudio.Workload.Universal

**Описание.** Создание приложений для универсальной платформы Windows с помощью C#, VB, JavaScript или C++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.WebSocket | WebSocket4Net | Обязательное
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Component.NetFX.Native | .NET Native | Обязательное
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | Обязательное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Обязательное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Обязательное
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | Обязательное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Обязательное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Обязательное
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Microsoft.VisualStudio.Component.UWP.Support | Средства универсальной платформы Windows (2.0) | Обязательное
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Обязательное
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Обязательное
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Средства универсальной платформы Windows для Cordova (2.0) | Обязательное
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin (2.0) | Обязательное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Рекомендованное
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | Optional
Microsoft.VisualStudio.Component.CodeClone | Клон кода | Optional
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | Optional
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Пакет SDK графических инструментов для Windows 8.1 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Эмулятор Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Средства универсальной платформы Windows для C++ | Optional


## <a name="visual-studio-extension-development"></a>Разработка расширений Visual Studio

**Идентификатор.** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Описание.** Создание надстроек и расширений для Visual Studio. Содержит новые команды, анализаторы кода и окна инструментов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Обязательное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Обязательное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Обязательное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | Обязательное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | Обязательное
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | Обязательное
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Необходимые компоненты для разработки расширений Visual Studio | Обязательное
Microsoft.VisualStudio.Component.CodeClone | Клон кода | Рекомендованное
Microsoft.VisualStudio.Component.CodeMap | Представление кода | Рекомендованное
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Динамическая проверка зависимостей | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Рекомендованное
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | Рекомендованное
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.NCLI | Собственный клиент SQL Server | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Инструменты архитектуры и анализа | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | Optional
Microsoft.VisualStudio.Component.DslTools | Пакет SDK для моделирования | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Optional
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | Optional
Microsoft.VisualStudio.Component.VC.ATL | Поддержка библиотеки ATL для Visual C++ | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Поддержка библиотек MFC и ATL (x86 и x64) | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.VSSDK | SDK для Visual Studio | Optional


## <a name="mobile-development-with-javascript"></a>Разработка мобильных приложений на языке JavaScript

**Идентификатор.** Microsoft.VisualStudio.Workload.WebCrossPlat

**Описание.** Разработка приложений Android, iOS и UWP с помощью средств для Apache Cordova.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Component.CordovaToolset.6.3.1 | Набор инструментов Cordova 6.3.1 | Обязательное
Component.WebSocket | WebSocket4Net | Обязательное
Microsoft.VisualStudio.Component.Cordova | Основные компоненты для разработки мобильных приложений на JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | Обязательное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | Обязательное
Microsoft.VisualStudio.Component.TypeScript.2.1 | Пакет SDK для TypeScript 2.1 | Обязательное
Component.Android.SDK23 | Установка пакета SDK для Android (уровень API 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Эмулятор Google Android (уровень API 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.JavaJDK | Пакет разработки для Java SE (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования | Optional
Microsoft.VisualStudio.Component.Git | Git для Windows | Optional
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Эмулятор Windows 10 Mobile (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Средства универсальной платформы Windows для Cordova (2.0) | Optional
## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | Имя
--- | ---
Component.GitHub.VisualStudio | Расширение GitHub для Visual Studio
Microsoft.Component.Blend.SDK.WPF | Blend для пакета SDK для Visual Studio для .NET
Microsoft.Component.HelpViewer | Help Viewer
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5
Microsoft.VisualStudio.Component.DependencyValidation.Community | Проверка зависимостей
Microsoft.VisualStudio.Component.LinqToSql | Инструменты LINQ to SQL
Microsoft.VisualStudio.Component.TestTools.Core | Основные компоненты средств тестирования
Microsoft.VisualStudio.Component.TypeScript.2.0 | Пакет SDK для TypeScript 2.0

## <a name="see-also"></a>См. также

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)

