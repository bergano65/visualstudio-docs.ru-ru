---
title: Перенос, миграция и обновление проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: e78062acfa95c48f0e95f18f42b2c1b26d1f3fa2
ms.sourcegitcommit: 86e1b3eca4633c7522b48282ff7a2be7a09296dd
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548229"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Перенос, миграция и обновление проектов Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самую актуальную документацию по Visual Studio см. в статье [Ссылка на сведения о миграции и обновлении проекта для Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

При рассмотрении необходимости перехода на более новую версию Visual Studio можно воспользоваться этой статьей, чтобы узнать, какие решения, проекты, файлы и другие ресурсы, созданные в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 SP1, будут запущены. без изменения в Visual Studio 2013 и Visual Studio 2015. Или же вы могли быть перенаправлены на эту страницу, если поступило сообщение об ошибке при попытке открыть проект, который не поддерживается в используемой версии Visual Studio либо требует наличия пакета SDK или расширения, такого как Azure SDK для .NET.

Многие широко используемые активы ведут себя одинаково в Visual Studio 2015, Visual Studio 2013 и двух предыдущих версиях. Например, в Visual Studio 2015 можно открыть проект, созданный в Visual Studio 2013 или Visual Studio 2012, изменить его, а затем снова открыть в Visual Studio 2015. Изменения сохраняются, и проект ведет себя так же, как и в более ранней версии. То же самое верно для многих других активов, созданных в Visual Studio 2010 с пакетом обновления 1 (SP1).

Для Visual Basic в Visual Studio 2015 не были внесены изменения, которые помешать Visual Basicному приложению, созданному в Visual Studio 2013 компиляции. Поведение во время выполнения Visual Basic приложений, которые перекомпилируются с помощью Visual Studio 2015, не изменятся.

Если вы используете Visual Studio 2015 вместе с Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1), можно создавать и изменять проекты и файлы в любой из указанных версий. Проекты и файлы можно переносить между версиями при условии, что не добавляются компоненты, которые не поддерживаются в одной или нескольких версиях.

## <a name="project"></a> Проекты

В следующем списке описывается поддержка в Visual Studio 2015 и Visual Studio 2013 для проектов, созданных в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1). Используйте этот список, чтобы определить, можно ли открыть проект "как есть" в Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1), или же необходимо изменить его для обеспечения совместимости.

|Тип проекта|Совместимость|
|---------------------|-------------------|
|Приложения универсальной платформы Windows|Чтобы установить средства для разработки универсальных приложений для Windows, в программе установки Visual Studio установите переключатель **Настраиваемая** или **Изменить**и выберите компонент **Средства разработки универсальных приложений Windows**.<br /><br /> Разработка приложений универсальная платформа Windows (UWP) для Windows 10 поддерживается только в Visual Studio 2015 в Windows 10 или [!INCLUDE[win81](../includes/win81-md.md)].|
|Приложения для Магазина Windows|Разработку приложений для Магазина Windows, включая универсальные приложения, работающие как на Windows 8.1, так и на Windows Phone 8.1, поддерживают [!INCLUDE[win81](../includes/win81-md.md)] и Windows 10. Существующие проекты [!INCLUDE[win8](../includes/win8-md.md)] могут по-прежнему обслуживаться, но создавать новые проекты [!INCLUDE[win8](../includes/win8-md.md)] будет невозможно. Проекты [!INCLUDE[win81](../includes/win81-md.md)] могут зависеть только от некоторых типов ссылок. Дополнительные сведения см. в статье [Управление ссылками в проекте](../ide/managing-references-in-a-project.md). **Примечание.** [!INCLUDE[win81](../includes/win81-md.md)] проекты, созданные с помощью visual Studio 2015 или Visual Studio 2013, не могут быть открыты в visual Studio 2012. Это связано с тем, что [!INCLUDE[win81](../includes/win81-md.md)] проекты, созданные с помощью Visual Studio 2015 и Visual Studio 2013 предназначены для этих версий, а Visual Studio 2012 поддерживает только проекты [!INCLUDE[win8](../includes/win8-md.md)], предназначенные для [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Вы можете создавать и использовать эти проекты в Visual Studio 2015 и Visual Studio 2013 после установки соответствующего пакета с несколькими настройками. Эти проекты не поддерживаются в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Эти проекты можно создавать и открывать в Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012, но не в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|BizTalk|Проекты BizTalk Server несовместимы с Visual Studio 2015 или Visual Studio 2013.|
|Приложение или библиотека классов Silverlight 4 C#/Visual Basic|Если разрешить Visual Studio автоматически обновлять проект, его можно открыть либо в Visual Studio 2013, либо в Visual Studio 2012.|
|Веб-форма или форма Windows C#/Visual Basic|Проект можно открыть в Visual Studio 2013 и Visual Studio 2012.|
|Visual Basic 6 и Visual C++ 6|Visual Studio 2012 и Visual Studio 2013 не поддерживают отладку приложений, созданных с помощью Visual Basic 6 C++ или Visual 6; для отладки этих приложений используйте более ранние версии Visual Studio.|
|Закодированный тест ИП|Если разрешить Visual Studio автоматически обновлять проект, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|F#|Если вы разрешаете Visual Studio обновить проект, созданный в Visual Studio 2010 с пакетом обновления 1 (SP1), его можно открыть в Visual Studio 2013 и Visual Studio 2012. Однако вы не можете обновить проект Silverlight, созданный в более ранней версии Visual Studio, для Visual Studio 2013. Вместо этого необходимо создать проект Silverlight в Visual Studio 2013 а затем скопировать в него свой код. Проекты Silverlight, создаваемые в Visual Studio 2013 целевом Silverlight 5.|
|LightSwitch|Если разрешить Visual Studio автоматически обновлять проект, его можно открыть только в Visual Studio 2013.|
|Кэш локальной базы данных|Шаблон локального кэша базы данных и диалоговое окно **Настройка синхронизации данных** не включаются в Visual Studio 2013. Visual Studio 2013 можно использовать для открытия и запуска проектов, созданных в [!INCLUDE[vs2010](../includes/vs2010-md.md)] если установлены службы синхронизации Майкрософт версии 1.0, но если вы хотите обновить их в Visual Studio 2013, необходимо внести все изменения вручную в коде. В качестве альтернативы можно продолжать использовать [!INCLUDE[vs2010](../includes/vs2010-md.md)] для ведения и обновления этих проектов.  При разработке новых проектов ориентируйтесь на новую модель синхронизации, предоставляемую Microsoft Sync Framework. Сведения см. в разделе [Центр разработчиков Microsoft Sync Framework](https://msdn.microsoft.com/sync/default)|
|Платформа MVC ("модель-представление-контроллер")|Visual Studio 2010 с пакетом обновления 1 (SP1) поддерживает только MVC 2 и MVC 3, Visual Studio 2012 поддерживает только MVC 3 и MVC 4, а Visual Studio 2013 поддерживает только MVC 4. Сведения об автоматическом обновлении MVC 2 до MCV 3 см. в разделе [Средство обновления приложения MVC 3 ASP.NET](https://go.microsoft.com/fwlink/?LinkID=238178). Сведения об обновлении MVC 2 до MVC 3 вручную см. в разделе [Обновление проекта ASP.NET MVC 2 до обновления инструментов ASP.NET MVC 3](https://go.microsoft.com/fwlink/?linkid=238178). Сведения об обновлении MVC3 до MVC 4 вручную см. в разделе [Обновление проекта ASP.NET MVC 3 до ASP.NET MVC 4](https://docs.microsoft.com/aspnet/whitepapers/mvc4-release-notes). Если проект ориентирован на платформу .NET Framework 3.5 с пакетом обновления 1 (SP1), необходимо переориентировать его на .NET Framework 4.|
|Моделирование|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).<br /><br /> Когда сервер Team Foundation собирает проект моделирования, он пытается проверить слои в проекте. В Visual Studio 2013 Team Foundation Build не может проверить слои проекта моделирования, созданного в Visual Studio 2010 с пакетом обновления 1 (SP1). Однако в Visual Studio 2010 с пакетом обновления 1 (SP1) Team Foundation Build может проверить слои в проекте моделирования, созданном в Visual Studio 2013.|
|Отладка MPI-кластера|Если на компьютерах с Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1) установлена та же версия среды выполнения или средств, этот проект можно открыть во всех трех версиях.|
|Пакет установки (VDPROJ)|Невозможно открыть этот проект в Visual Studio 2013, так как он не поддерживает этот тип проекта. Рекомендуется использовать InstallShield Limited Edition для Visual Studio (ISLE), бесплатное решение для развертывания, которое поддерживает большинство сред выполнения приложений и платформ Windows. Также можно использовать ISLE для импорта данных и параметров из проектов установщиков Visual Studio. .|
|Office 2007 VSTO|При обновлении проекта до версии Office 2013 и .NET Framework 4 можно открыть этот проект в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Office 2010 VSTO|Если проект предназначен для .NET Framework 4, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Все остальные проекты требуют одностороннего обновления.|
|Полнофункциональные интернет-приложения|При обновлении проекта его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|SharePoint 2007|Не удается открыть этот проект в Visual Studio 2013. Однако при ручном обновлении проекта до SharePoint 2010 его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Дополнительные сведения об обновлении SharePoint 2007 см. в статьях [Миграция с SharePoint 2007 в SharePoint 2010 для ИТ-специалистов](https://go.microsoft.com/fwlink/?LinkId=238224) и [Поиск в корпоративной среде SharePoint](https://docs.microsoft.com/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|SketchFlow|Если вы разрешаете Visual Studio обновить проект до WPF 4.5 или Silverlight 5, вы можете открыть его в Visual Studio 2012 и Visual Studio 2013.|
|База данных [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|Проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Если имеется файл базы данных, (MDF), созданный в более ранней версии SQL Server, необходимо обновить ее в [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] , прежде чем его можно будет использовать с базой данных LocalDB SQL Server Express, но база данных больше не будет совместима с предыдущими версиями SQL Server. Если не выполнить обновление, можно продолжить работу с базой данных в Visual Studio 2013, установив и используя [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] на том же компьютере. Дополнительные сведения см. в статье [Обновление MDF-файлов](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Если на компьютерах под управлением Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1) установлен [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express, можно открыть проект во всех трех версиях.|
|Проект отчетов SQL Server|Проект можно открыть в Visual Studio 2013 и Visual Studio 2012. Если используется только локальный режим (то есть без подключения к SQL Server), у пользователя нет возможности использования элементов управления, связанных со средством просмотра в [!INCLUDE[vs2010](../includes/vs2010-md.md)], во время разработки, однако сам проект функционирует корректно во время выполнения. **Внимание!**  Если добавить функцию, относящуюся к Visual Studio 2013, схема отчета обновляется автоматически, и вы больше не сможете открыть проект в Visual Studio 2012.|
|Модульные тесты|Для открытия тестов, созданных в любой из этих версий, можно использовать [!INCLUDE[TCMext](../includes/tcmext-md.md)] в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Visual C++|Visual Studio 2013 можно использовать для открытия C++ проекта, созданного в visual Studio 2012 или visual Studio 2010 с пакетом обновления 1 (SP1). Если вы хотите использовать среду сборки Visual Studio 2013 для создания проекта, созданного в Visual Studio 2012, на одном компьютере должны быть установлены обе версии Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) и [Руководство по переносу и обновлению Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 web|Если разрешить Visual Studio автоматически обновлять проект, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|База данных Visual Studio 2010 (DBPROJ)|При преобразовании проекта в SQL Server Data Tools проект базы данных его можно открыть в Visual Studio 2013. Однако Visual Studio 2013 не поддерживает эти артефакты:<br /><br /> — модульные тесты;<br />— планы создания данных;<br />— файлы сравнения данных;<br />— пользовательские расширения правил для анализа статического кода;<br />— server.sqlsettings;<br />— SQLCMD-файлы;<br />— пользовательские расширения развертывания;<br />— частичные проекты (.files).<br /><br /> Если установить SQL Server Data Tools, можно открыть проект в Visual Studio 2010 с пакетом обновления 1 (SP1) после преобразования. Дополнительные сведения см. в разделе [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Визуальные инструменты для баз данных в Visual Studio 2010|Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Visual Studio Lab Management|Для открытия сред, созданных в любой из этих версий, можно использовать [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Однако версия Microsoft Test Manager должна соответствовать версии Team Foundation Server, чтобы можно было создавать среды.|
|Макрос Visual Studio|Невозможно открыть этот проект в Visual Studio 2013, так как он не поддерживает тип проекта.|
|SDK для Visual Studio/VSIX|После обновления проекта пакета SDK для Visual Studio до Visual Studio 2013 он не может быть открыт в Visual Studio 2012. Дополнительные сведения см. в разделе [Практическое руководство. перенести проекты расширяемости в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Инструменты Microsoft Azure для Visual Studio|Если вы используете Microsoft Azure Tools для Visual Studio версии 2,1, можно открыть проект в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Для проектов, предназначенных для более ранних версий, если вы разрешаете Visual Studio обновить проект до версии 2,1, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Windows Communication Foundation, Windows Presentation Foundation|Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Windows Mobile|Невозможно открыть этот проект в Visual Studio 2013, так как он не поддерживает тип проекта.|
|Windows Phone 7.1|Если вы разрешаете Visual Studio обновить проект до Windows Phone 8,0, его можно открыть в Visual Studio 2012 и Visual Studio 2013.|
|Другой|Большинство типов проектов можно открывать в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Веб-сайты FrontPage|Невозможно открыть этот проект в Visual Studio 2013, так как он не поддерживает тип проекта.|
|Переносимая библиотека классов|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).<br /><br /> — Проекты, ориентированные на Silverlight 4, ориентированы и на Silverlight 5.<br />— Проекты для Windows Phone 7.0 или Windows Phone 7.5 ориентированы и на Windows Phone 8.<br />— Проекты, ориентированные на Xbox 360, более не будут ориентированы на Xbox 360.|
|Проекты Azure, такие как проекты облачных служб (с расширением CCPROJ) и проекты диспетчера ресурсов Azure (проекты облачного развертывания) с расширением DEPLOYPROJ|Для открытия этих типов проектов сначала установите [пакет Azure SDK для .NET](https://azure.microsoft.com/downloads/), а затем откройте соответствующий проект.|

## <a name="troubleshooting-project-compatibility-issues"></a>Устранение проблем совместимости проектов
 Ниже приведены некоторые действия, которые можно выполнить, если проект не открывается в Visual Studio 2015 или Visual Studio 2013.

- При попытке открыть проект, который не поддерживается в Visual Studio 2015 или Visual Studio 2013 и для которого не установлена соответствующая версия Visual Studio, может появиться сообщение о том, что тип проекта не поддерживается, и тип проекта может быть указан в диалоговом окне **Проверка изменений проекта и решения** в разделе **неподдерживаемые проекты**. Для устранения этой проблемы откройте страницу программ и компонентов на **панели управления**Windows, выберите **Visual Studio**, а затем выберите **Изменить**и **Восстановить**. Затем можно будет установить отсутствующую версию.

- При попытке открыть проект для классического приложения в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] возникает ошибка и отображается одно из следующих сообщений: "Этот выпуск Visual Studio поддерживает только приложения [!INCLUDE[win81](../includes/win81-md.md)]" или "Этот проект несовместим с текущим выпуском Visual Studio". Версия [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] предназначена для разработки, тестирования и развертывания приложений Магазина Windows, созданных для Windows 8.1. Чтобы открыть проект классического приложения, необходимо использовать выпуск Visual Studio, поддерживающий этот тип проекта.

   Дополнительные сведения о выпусках Visual Studio см. в описании [продуктов Microsoft Visual Studio](https://visualstudio.microsoft.com/products/).

- При попытке открыть проект приложения для Магазина Windows в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, возникает ошибка. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop нельзя использовать для создания приложений для Магазина Windows. Если требуется создавать приложения для Магазина Windows, можно также установить [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. А для разработки приложений для всех платформ Microsoft и Интернета попробуйте Visual Studio Professional 2013.

- Если для проекта требуются функции, характерные для Visual Studio 2013, он не может быть открыт в более ранней версии.

- Если вы используете Visual Studio 2012 и хотите открыть проект, созданный в Visual Studio 2013, можно настроить систему проекта для включения функций Visual Studio 2013. Дополнительные сведения см. в статье [Обеспечение поддержки версий в пользовательских проектах](../misc/making-custom-projects-version-aware.md).

  Дополнительные сведения об устранении неполадок см. в статье базы знаний [Совместимость Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="file"></a> Файлы

В следующем списке указано, поддерживает ли Visual Studio 2013 каждый тип файла, можно ли открыть его в Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1), а также нужно ли изменить его для обеспечения совместимости.

|Тип файлов|Совместимость|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (XML-файлы)|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Схемы неструктурированных файлов BizTalk|Эти схемы можно добавить в проект BizTalk 2013 в Visual Studio 2013. Чтобы использовать Visual Studio 2013 с проектами BizTalk 2010, которые имеют схемы неструктурированных файлов, установите BizTalk 2013 на компьютере с Visual Studio 2013. При первом открытии проекта BizTalk 2010 он автоматически обновляется до версии BizTalk 2013 или Visual Studio 2013 системы проектов.|
|Файлы определений клиентских отчетов (RDLC)|Эти файлы можно открыть в Visual Studio 2013, и схема будет автоматически обновлена при добавлении Visual Studio 2013 компонентов и элементов управления.|
|Наборы правил анализа кода|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы пакетов приложений уровня данных|Эти файлы можно открыть в Visual Studio 2013, если они имеют версию 2,0 или 2,5.|
|Файлы дампов отладчика|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы диаграмм DGML|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1), не изменяя файл.|
|Файлы моделей данных с использованием сущностей (EDMX)|В Visual Studio 2013 можно открыть файл EDMX, предназначенный для .NET Framework 4,5 или .NET Framework 4 без изменения файла.|
|Файлы отчетов профилировщика|Файлы отчетов профилировщика (VSP. VSPS,. PSESS и. VSPF) можно открыть в Visual Studio 2012 и Visual Studio 2013. VSPX-файлы невозможно открывать в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файл решения (SUO)|Visual Studio 2013 можно использовать для открытия файла решения, созданного в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1)|
|SQL Server Compact Edition|Visual Studio 2013 не поддерживает SQL Server Compact Edition.|
|SQLX-файлы|Чтобы открыть эти файлы в Visual Studio 2013, необходимо выполнить одностороннее обновление, развернуть склкс-файл в целевой версии Visual Studio, а затем перестроить файл в формате DACPAC.|
|Файлы журналов IntelliTrace из [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы анализатора памяти JavaScript (DIAGSESSION)|Файлы, созданные в более ранних версиях Visual Studio, можно просмотреть в Visual Studio 2013. Однако в зависимости от собираемых данных файлы, созданные в Visual Studio 2013, могут не открываться в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).|

## <a name="integration"></a> Активы интеграции

Проблемы совместимости могут возникнуть при использовании клиентов и серверов из разных версий Visual Studio Team Foundation Server.

|Тип интеграции|Совместимость|
|-------------------------|-------------------|
|"Проверка кода" и "Моя работа"|Функции "Проверка кода" и "Моя работа" не будут работать при подключении клиента [!INCLUDE[esprfound](../includes/esprfound-md.md)] к [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|64-разрядную среду, такую как MSBuild или [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] , невозможно использовать для сборки приложений [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , создаваемых в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>См. также

- [Обеспечение поддержки версий в пользовательских проектах](../misc/making-custom-projects-version-aware.md)
