---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Desktop Express
titleSuffix: ''
description: Идентификаторы рабочих нагрузок и компонентов позволяют устанавливать Visual Studio с помощью командной строки. Также их можно указать в качестве зависимости в манифесте VSIX.
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 21735c82a318623758f1980a1865a543adde121e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881806"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Каталог компонентов Visual Studio Desktop Express

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки или в качестве зависимости в манифесте VSIX. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты.
* По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Когда вы включаете зависимости в манифест VSIX, достаточно указать только идентификаторы компонентов. Таблицы на этой странице позволяют определить минимальный набор зависимостей компонентов. В некоторых сценариях нужно указать лишь один компонент из рабочей нагрузки. В других случаях потребуется несколько компонентов из одной рабочей нагрузки или несколько компонентов из нескольких рабочих нагрузок. Дополнительные сведения см. в статье [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Руководство по переносу проектов расширения среды на Visual Studio 2017).

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express для Windows Desktop

**Идентификатор:** Microsoft.VisualStudio.Workload.WDExpress

**Описание:** сборка собственных и управляемых приложений, таких как WPF, WinForms и Win32 с возможностью редактирования кода с учетом синтаксиса, а также управления исходным кодом и рабочими элементами. Включает поддержку C#, Visual Basic и Visual C++.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Компонент для публикации ClickOnce | 15.8.27825.0 | Обязательно
Microsoft.Component.HelpViewer | Окно справки | 15.6.27323.2 | Обязательно
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Обязательно
Microsoft.Component.VC.Runtime.OSSupport | Среда выполнения Visual C++ для UWP | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.8.27825.0 | Обязательно
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.Common.Azure.Tools | Средства подключения и публикации | 15.9.28107.0 | Обязательно
Microsoft.VisualStudio.Component.CoreEditor | Основной редактор Visual Studio | 15.8.27729.1 | Обязательно
Microsoft.VisualStudio.Component.EntityFramework | Инструменты для Entity Framework 6 | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet | Диспетчер пакетов NuGet | 15.9.28016.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# и Visual Basic | 15.8.27729.1 | Обязательно
Microsoft.VisualStudio.Component.SQL.ADAL | Среда выполнения SQL ADAL | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.SQL.CLR | Типы данных среды CLR для SQL Server | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.SQL.CMDUtils | Служебные программы командной строки SQL Server | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.SQL.DataSources | Источники данных для поддержки SQL Server | 15.0.26621.2 | Обязательно
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB для экспресс-выпуска SQL Server 2016 | 15.7.27617.1 | Обязательно
Microsoft.VisualStudio.Component.SQL.NCLI | собственный клиент SQL Server | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Обязательно
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.TextTemplating | Преобразование текстовых шаблонов | 15.0.26208.0 | Обязательно
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | 15.6.27309.0 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | 15.8.27825.0 | Обязательно
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Компиляторы и библиотеки Visual C++ для ARM64 | 15.9.28230.55 | Обязательно
Microsoft.VisualStudio.Component.VisualStudioData | Источники данных и ссылки на службы | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.6.27406.0 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Пакет SDK для Windows 10 (10.0.17134.0) | 15.8.27924.0 | Обязательно

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | Имя | Версия
--- | --- | ---
Недоступно | Недоступно | Недоступно

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
