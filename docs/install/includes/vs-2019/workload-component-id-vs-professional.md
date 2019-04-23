---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Professional 2019
titleSuffix: ''
description: Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX.
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 04/02/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 23cbd90b81bcc05fef34040b4934c7152f79ae41
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2019
ms.locfileid: "58873033"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Основной редактор Visual Studio (входит в состав Visual Studio Professional 2019)

**Идентификатор:** Microsoft.VisualStudio.Workload.CoreEditor

**Описание.** Основные возможности оболочки Visual Studio, включая редактирование кода с учетом синтаксиса, управление исходным кодом и рабочими элементами.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Основной редактор Visual Studio | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Начальная страница Visual Studio для пользователей C++ | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Разработка для Azure

**Идентификатор:** Microsoft.VisualStudio.Workload.Azure

**Описание.** Пакеты Azure SDK, инструменты и проекты для разработки облачных приложений, создания ресурсов и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Обязательно
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.0.28714.129 | Обязательно
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 16.0.28516.191 | Обязательно
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.0.28720.110 | Обязательно
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Необходимые компоненты для разработки на базе Azure | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 16.0.28720.110 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Средства Visual Studio для Kubernetes | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Основные инструменты Azure Resource Manager | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Средства Service Fabric | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Инструменты облачных служб Azure | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Средства Azure Resource Manager | 16.0.28528.71 | Рекомендованное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Средства разработки .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy службы хранилища Azure | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Хранение и обработка данных

**Идентификатор:** Microsoft.VisualStudio.Workload.Data

**Описание.** Связывание, разработка и тестирование решений по обработке данных с помощью SQL Server, Azure Data Lake и Hadoop.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Рекомендованное
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Рекомендованное
Microsoft.Component.Azure.DataLake.Tools | Средства Azure Data Lake и Stream Analytics | 16.0.28720.110 | Рекомендованное
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.0.28720.110 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Рекомендованное
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Приложения для обработки и анализа данных и аналитические приложения

**Идентификатор:** Microsoft.VisualStudio.Workload.DataScience

**Описание.** Языки и средства для создания приложений для обработки и анализа данных, включая Python и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.PythonTools | Поддержка языка Python | 16.0.28625.61 | Рекомендованное
Microsoft.Component.PythonTools.Minicondax64 | Python Miniconda | 16.0.28625.61 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Рекомендованное
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC версии 140 — средства сборки C++ VS 2015 (версия 14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="net-desktop-development"></a>Разработка классических приложений .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Описание.** Создание WPF, форм Windows Forms и консольных приложений с помощью C#, Visual Basic и F#.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 16.0.28315.86 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 16.0.28315.86 | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Средства разработки .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | Поддержка языка F# для классических приложений | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Пакет нацеливания переносимой библиотеки .NET | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Optional

## <a name="game-development-with-unity"></a>Разработка игр с помощью Unity

**Идентификатор:** Microsoft.VisualStudio.Workload.ManagedGame

**Описание.** Создание двухмерных и трехмерных игр с помощью Unity, мощной кроссплатформенной среды разработки.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Unity | Набор средств Visual Studio для Unity | 16.0.28315.86 | Обязательно
Component.UnityEngine.x64 | Редактор Unity 2018.3 (64-разрядный) | 16.0.28707.178 | Рекомендованное
Component.UnityEngine.x86 | Редактор Unity 5.6 (32-разрядный) | 16.0.28707.178 | Рекомендованное

## <a name="linux-development-with-c"></a>Разработка приложений для Linux на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Описание.** Создание и отладка приложений, запускаемых в среде Linux.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.MDD.Linux | Разработка на C++ для Linux | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.0.28315.86 | Обязательно
Component.Linux.CMake | Средства CMake C++ для Linux | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Рекомендованное
Component.MDD.Linux.GCC.arm | Средства разработки для встроенных платформ и Интернета вещей | 16.0.28625.61 | Optional

## <a name="desktop-development-with-c"></a>Разработка классических приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeDesktop

**Описание.** Создание классических приложений Windows с помощью набора инструментов Microsoft C++, ATL или MFC.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Обновление для распространяемого компонента C++ 2019 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Основные возможности Visual C++ для классических приложений | 16.0.28315.86 | Обязательно
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Microsoft.VisualStudio.Component.Debugger.JustInTime | JIT-отладчик | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.ATL | ATL C++ для средств сборки версии 142 (x86 и x64) | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Средства CMake C++ для Windows | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Адаптер теста для Boost.Test | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Адаптер тестов для Google Test | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Рекомендованное
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC версии 140 — средства сборки C++ VS 2015 (версия 14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC C++ для средств сборки версии 142 (x86 и x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI для средств сборки версии 142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули C++ для средств сборки версии 142 (x64 или x86 — экспериментальная) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC версии 141 — средства сборки C++ для VS 2017 для x64 или x86 (версия 14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="game-development-with-c"></a>Разработка игр на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeGame

**Описание.** Используйте все возможности C++ для создания профессиональных игр на базе DirectX, Unreal или Cocos2D.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Обновление для распространяемого компонента C++ 2019 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Рекомендованное
Component.Android.NDK.R16B | NDK для Android (R16B) | 16.0.28728.38 | Optional
Component.Android.SDK25.Private | Установка пакета SDK для Android (уровень API 25) (локальная установка для разработки мобильных приложений на C++) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.Android | Средства разработки на C++ для Android | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.0.28625.61 | Optional
Component.Unreal | Установщик Unreal Engine | 16.0.28625.61 | Optional
Component.Unreal.Android | Поддержка IDE Android для Unreal Engine | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Разработка мобильных приложений на C++

**Идентификатор:** Microsoft.VisualStudio.Workload.NativeMobile

**Описание.** Создание межплатформенных приложений для iOS, Android или Windows на С++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Android.SDK25.Private | Установка пакета SDK для Android (уровень API 25) (локальная установка для разработки мобильных приложений на C++) | 16.0.28625.61 | Обязательно
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Обязательно
Component.Android.NDK.R16B | NDK для Android (R16B) | 16.0.28728.38 | Рекомендованное
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Рекомендованное
Component.MDD.Android | Средства разработки на C++ для Android | 16.0.28517.75 | Рекомендованное
Component.Android.NDK.R16B_3264 | NDK для Android (R16B) (32-разрядный) | 16.0.28728.38 | Optional
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (уровень API 25), локальная установка | 16.0.28625.61 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), локальная установка | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild — ускорение сборки | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.IOS | Средства разработки C++ для iOS | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Кроссплатформенная разработка .NET Core

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCoreTools

**Описание.** Создание кроссплатформенных приложений с помощью .NET Core, ASP.NET Core, HTML, JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Обязательно
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 16.0.28516.191 | Обязательно
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.0.28714.129 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.0.28720.110 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.0.28621.142 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 16.0.28621.142 | Рекомендованное
Microsoft.Net.Core.Component.SDK.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Средства разработки .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 16.0.28315.86 | Optional

## <a name="mobile-development-with-net"></a>Разработка мобильных приложений на платформе .NET

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Описание.** Создание кроссплатформенных приложений для iOS, Android или Windows с помощью Xamarin.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Xamarin | Xamarin | 16.0.28625.61 | Обязательно
Component.Xamarin.RemotedSimulator | Симулятор удаленной работы для Xamarin | 16.0.28315.86 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 16.0.28516.191 | Обязательно
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.Merq | Внутренние средства Common Xamarin | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.MonoDebugger | Отладчик Mono | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Модуль создания шаблонов ASP.NET | 16.0.28315.86 | Обязательно
Component.Android.SDK27 | Программа установки пакета SDK для Android (уровень API 27) | 16.0.28517.75 | Рекомендованное
Component.OpenJDK | OpenJDK (дистрибутив от Майкрософт) | 16.0.28625.61 | Рекомендованное

## <a name="aspnet-and-web-development"></a>ASP.NET и веб-разработка

**Идентификатор:** Microsoft.VisualStudio.Workload.NetWeb

**Описание.** Создание веб-приложений с помощью ASP.NET, ASP.NET Core, HTML, JavaScript и контейнеров, включая поддержку Docker.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Обязательно
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Средства разработки .NET Core 2.1 | 16.0.28516.191 | Обязательно
Microsoft.NetCore.ComponentGroup.Web.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.FSharp | Поддержка языка F# | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Поддержка языка F# для веб-проектов | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Component.Microsoft.VisualStudio.Web.AzureFunctions | Средства веб-заданий Azure | 16.0.28714.129 | Рекомендованное
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 16.0.28516.191 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.AspNet45 | Дополнительные возможности ASP.NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.0.28720.110 | Рекомендованное
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Средства веб-заданий Azure | 16.0.28621.142 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Облачные средства для веб-разработки | 16.0.28621.142 | Рекомендованное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Средства разработки .NET Core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Средства разработки .NET Core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Дополнительные шаблоны проектов (предыдущие версии) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Поддержка времени разработки в IIS | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Разработка Node.js

**Идентификатор:** Microsoft.VisualStudio.Workload.Node

**Описание.** Создание масштабируемых сетевых приложений при помощи Node.js, асинхронной среды выполнения JavaScript с управлением на основе событий. 

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Node.Tools | Средства разработки для Node.js | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Optional

## <a name="officesharepoint-development"></a>Разработка для Office и SharePoint

**Идентификатор:** Microsoft.VisualStudio.Workload.Office

**Описание.** Создание надстроек для Office 365 и SharePoint, решений SharePoint и надстроек VSTO на C#, VB и JavaScript.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Обязательно
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Средства разработки классических приложений .NET | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Sharepoint.Tools | Инструменты разработчика Office для Visual Studio | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.TeamOffice | Набор средств Visual Studio для Office (VSTO) | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Средства разработки .NET Framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Разработка на Python

**Идентификатор:** Microsoft.VisualStudio.Workload.Python

**Описание.** Редактирование, отладка, интерактивная разработка и система управления версиями для Python.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.PythonTools | Поддержка языка Python | 16.0.28625.61 | Обязательно
Component.CPython3.x64 | 64-разрядная версия Python 3 (3.7.2) | 3.7.2 | Рекомендованное
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Рекомендованное
Microsoft.Component.PythonTools.Minicondax64 | Python Miniconda | 16.0.28625.61 | Рекомендованное
Microsoft.Component.PythonTools.Web | Поддержка веб-приложений Python | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 16.0.28315.86 | Рекомендованное
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Рекомендованное
Component.CPython2.x64 | 64-разрядная версия Python 2 (2.7.15) | 2.7.15 | Optional
Component.CPython2.x86 | 32-разрядная версия Python 2 (2.7.15) | 2.7.15 | Optional
Component.CPython3.x86 | 32-разрядная версия Python 3 (3.7.2) | 3.7.2 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Службы языка Razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Диспетчер библиотек | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Встроенные средства разработки Python | 16.0.28621.142 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Средства разработки для Azure | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Библиотеки Azure для .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Эмулятор вычислений Azure | 16.0.28720.110 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Эмулятор хранения Azure | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Основные инструменты облачных служб Azure | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Средства сборки облачных служб Azure | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Средства разработки контейнеров | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Основные средства рабочей нагрузки управляемого рабочего стола | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Драйвер SQL Server ODBC | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Служебные программы командной строки SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC версии 140 — средства сборки C++ VS 2015 (версия 14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Средства профилирования C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET и средства веб-разработки | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Предварительные требования для ASP.NET и средств веб-разработки | 16.0.28621.142 | Optional

## <a name="universal-windows-platform-development"></a>Разработка с помощью универсальной платформы Windows

**Идентификатор:** Microsoft.VisualStudio.Workload.Universal

**Описание.** Вы сможете создавать приложения для универсальной платформы Windows на C#, VB или, при необходимости, на C++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.0.28315.86 | Обязательно
Microsoft.ComponentGroup.Blend | Blend для Visual Studio | 16.0.28315.86 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 16.0.28517.75 | Обязательно
Microsoft.Net.Core.Component.SDK.2.1 | Средства разработки .NET Core 2.1 | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Graphics | Редакторы изображений и трехмерных моделей | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Диагностика JavaScript | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Поддержка языков JavaScript и TypeScript | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.Component.TypeScript.3.3 | Пакет SDK для TypeScript 3.3 | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Пакет SDK для Windows 10 (10.0.17763.0) | 16.0.28517.75 | Обязательно
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native и .NET Standard | 16.0.28516.191 | Обязательно
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Средства универсальной платформы Windows | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Средства универсальной платформы Windows для Xamarin | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 16.0.28621.142 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения универсальной платформы Windows C++ для средств сборки версии 142 | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Отладчик графики и профилировщик GPU для DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Поддержка универсальной платформы Windows C++ для средств сборки версии 142 (ARM64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Обновление для распространяемого компонента C++ 2019 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM (версия 14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC версии 142 — средства сборки C++ для VS 2019 для ARM64 (версия 14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC версии 141 — средства сборки C++ для VS 2017 для ARM (версия 14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC версии 141 — средства сборки C++ для VS 2017 для ARM64 (версия 14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC версии 141 — средства сборки C++ для VS 2017 для x64 или x86 (версия 14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Пакет SDK для Windows 10 (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Подключение USB-устройств | 16.0.28320.51 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Основные возможности Visual C++ для классических приложений | 16.0.28315.86 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Средства универсальной платформы Windows на C++ (версия 142) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Средства универсальной платформы Windows для C++ (v141) | 16.0.28621.142 | Optional

## <a name="visual-studio-extension-development"></a>Разработка расширений Visual Studio

**Идентификатор:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Описание.** Создавайте надстройки и расширения для Visual Studio, включая новые команды, анализаторы кода и окна инструментов.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.SDK | Пакет SDK для .NET Framework 4.7.2 | 16.0.28517.75 | Обязательно
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки для .NET Framework 4.7.2 | 16.0.28516.191 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 16.0.28714.129 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 16.0.28625.61 | Обязательно
Microsoft.VisualStudio.Component.VSSDK | SDK для Visual Studio | 16.0.28315.86 | Обязательно
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Необходимые компоненты для разработки расширений Visual Studio | 16.0.28621.142 | Обязательно
Microsoft.VisualStudio.Component.DiagnosticTools | Средства профилирования .NET | 16.0.28625.61 | Рекомендованное
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 16.0.28625.61 | Рекомендованное
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 16.0.28528.71 | Optional
Microsoft.Component.CodeAnalysis.SDK | Пакет SDK для .NET Compiler Platform | 16.0.28625.61 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения универсальной платформы Windows C++ для средств сборки версии 142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Средства анализа для разработчиков | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Конструктор классов | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.DslTools | Пакет SDK для моделирования | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.ATL | ATL C++ для средств сборки версии 142 (x86 и x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC C++ для средств сборки версии 142 (x86 и x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC версии 142 — средства сборки C++ для VS 2019 для x64 или x86 (версия 14.20) | 16.0.28625.61 | Optional

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Версия
--- | --- | ---
Component.GitHub.VisualStudio | Расширение GitHub для Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 16.0.28707.177
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | Средства разработки .NET Core 1.0–1.1 для веб-приложений | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Установщик интеграции Azure DevOps с Office | 16.0.28625.61
Microsoft.VisualStudio.Component.DependencyValidation.Community | Проверка зависимостей | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git для Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Редактор DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Инструменты LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL C++ для средств сборки версии 142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL C++ для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL C++ для средств сборки версии 142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL C++ для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL C++ для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC C++ для средств сборки версии 142 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC C++ для средств сборки версии 142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC C++ для средств сборки версии 142 с устранением рисков Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC C++ для средств сборки версии 142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | MFC C++ для средств сборки версии 142 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | Распространяемые пакеты MSM C++ 2019 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM с устранением рисков Spectre (версия 14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для ARM64 с устранением рисков Spectre (версия 14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC версии 142 — библиотеки C++ для VS 2019 для x64 или x86 с устранением рисков Spectre (версия 14.20)  | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для ARM с устранением рисков Spectre (версия 14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для ARM64 с устранением рисков Spectre (версия 14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL C++ для средств сборки версии 141 (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL C++ для средств сборки версии 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | ATL C++ для средств сборки версии 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | ATL C++ для средств сборки версии 141 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Поддержка C++/CLI для средств сборки версии 141 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC | MFC C++ для средств сборки версии 141 (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | MFC C++ для средств сборки версии 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | MFC C++ для средств сборки версии 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | MFC C++ для средств сборки версии 141 с устранением рисков Spectre (x86 и x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC версии 141 — библиотеки C++ для VS 2017 для x64 или x86 с устранением рисков Spectre (версия 14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Поддержка Windows XP на C++ для инструментов VS 2017 (версия 141) [не рекомендуется] | 16.0.28625.61
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.0.28621.142
