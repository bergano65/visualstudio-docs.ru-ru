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
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919093"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Перенос, миграция и обновление проектов Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самую актуальную документацию по Visual Studio см. в статье [Ссылка на сведения о миграции и обновлении проекта для Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Если вы принимаете решение о том, следует ли переходить на новую версию Visual Studio, с помощью этой статьи можно определить, какие решения, проекты, файлы и другие ресурсы, созданные в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1), будут без каких-либо изменений работать в Visual Studio 2013 и Visual Studio 2015. Или же вы могли быть перенаправлены на эту страницу, если поступило сообщение об ошибке при попытке открыть проект, который не поддерживается в используемой версии Visual Studio либо требует наличия пакета SDK или расширения, такого как Azure SDK для .NET.

Многие часто используемые ресурсы работают одинаково в Visual Studio 2015, Visual Studio 2013 и двух более ранних версиях. Например, в Visual Studio 2015 вы можете открыть проект, созданный в Visual Studio 2013 или Visual Studio 2012, изменить его, а затем снова открыть его в Visual Studio 2015. Изменения сохраняются, и проект ведет себя так же, как и в более ранней версии. То же самое верно для многих других активов, созданных в Visual Studio 2010 с пакетом обновления 1 (SP1).

Для Visual Basic в Visual Studio 2015 не внесено никаких изменений, которые будут препятствовать выполнению компиляции приложения Visual Basic, созданного в Visual Studio 2013. Поведение приложений Visual Basic, которые перекомпилированы с использованием Visual Studio 2015, во время выполнения не изменится.

Если вы используете Visual Studio 2015 вместе с Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1), можно создавать и изменять проекты и файлы в любой из указанных версий. Проекты и файлы можно перемещать между версиями, если не добавлять компоненты, которые не поддерживаются в одной или нескольких версиях.

## <a name="project"></a> Проекты

В следующем списке описывается поддержка Visual Studio 2015 и Visual Studio 2013 для проектов, созданных в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1). Этот список позволяет определить, можете ли вы открыть проект в Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1) в его текущем виде или же необходимо изменить его, чтобы обеспечить совместимость.

|Тип проекта|Совместимость|
|---------------------|-------------------|
|Приложения универсальной платформы Windows|Чтобы установить средства для разработки универсальных приложений для Windows, в программе установки Visual Studio установите переключатель **Настраиваемая** или **Изменить**и выберите компонент **Средства разработки универсальных приложений Windows**.<br /><br /> Разработку приложений универсальной платформы Windows (UWP) для Windows 10 поддерживает только Visual Studio 2015 на базе Windows 10 или [!INCLUDE[win81](../includes/win81-md.md)].|
|Приложения для Магазина Windows|Разработку приложений для Магазина Windows, включая универсальные приложения, работающие как на Windows 8.1, так и на Windows Phone 8.1, поддерживают [!INCLUDE[win81](../includes/win81-md.md)] и Windows 10. Существующие проекты [!INCLUDE[win8](../includes/win8-md.md)] могут по-прежнему обслуживаться, но создавать новые проекты [!INCLUDE[win8](../includes/win8-md.md)] будет невозможно. Проекты [!INCLUDE[win81](../includes/win81-md.md)] могут зависеть только от некоторых типов ссылок. Дополнительные сведения см. в статье [Управление ссылками в проекте](../ide/managing-references-in-a-project.md). **Примечание.** Проекты [!INCLUDE[win81](../includes/win81-md.md)], созданные с помощью Visual Studio 2015 или Visual Studio 2013, не могут быть открыты в Visual Studio 2012. Это происходит потому, что проекты [!INCLUDE[win81](../includes/win81-md.md)], созданные с помощью Visual Studio 2015 и Visual Studio 2013, предназначены для соответствующих версий, а Visual Studio 2012 поддерживает только проекты [!INCLUDE[win8](../includes/win8-md.md)], предназначенные для [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Эти проекты можно создавать и использовать в Visual Studio 2015 и Visual Studio 2013 после установки соответствующего пакета многоплатформенного нацеливания. Эти проекты не поддерживаются в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Эти проекты можно создавать и открывать в Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012, но не в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|BizTalk|Проекты сервера BizTalk несовместимы с Visual Studio 2015 и Visual Studio 2013.|
|Приложение или библиотека классов Silverlight 4 C#/Visual Basic|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013 или Visual Studio 2012.|
|Веб-форма или форма Windows C#/Visual Basic|Проект можно открыть в Visual Studio 2013 и Visual Studio 2012.|
|Visual Basic 6 и Visual C++ 6|Visual Studio 2012 и Visual Studio 2013 не поддерживают отладку приложений, собранных с использованием Visual Basic 6 или Visual C++ 6. Для отладки этих приложений используйте более ранние версии Visual Studio.|
|Закодированный тест ИП|Если разрешить автоматическое обновление проекта в Visual Studio, его можно будет открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|F#|Если разрешить Visual Studio обновить проект, созданный в Visual Studio 2010 с пакетом обновления 1 (SP1), его можно открыть в Visual Studio 2013 и Visual Studio 2012. Тем не менее невозможно обновить проект Silverlight, созданный в более старой версии Visual Studio, до Visual Studio 2013. Вместо этого необходимо создать проект Silverlight в Visual Studio 2013 и скопировать в него код. Проекты Silverlight, создаваемые в Visual Studio 2013, предназначены для Silverlight 5.|
|LightSwitch|Если разрешить Visual Studio обновить проект автоматически, его можно будет открыть только в Visual Studio 2013.|
|Кэш локальной базы данных|Шаблон кэша локальной базы данных и диалоговое окно **Настройка синхронизации данных** не входят в состав Visual Studio 2013. С помощью Visual Studio 2013 можно открыть и запустить проекты, созданные в [!INCLUDE[vs2010](../includes/vs2010-md.md)], если установлены службы Microsoft Synchronization Services версии 1.0. Однако если требуется обновить их в Visual Studio 2013, необходимо вручную внести изменения в код. В качестве альтернативы можно продолжать использовать [!INCLUDE[vs2010](../includes/vs2010-md.md)] для ведения и обновления этих проектов.  При разработке новых проектов ориентируйтесь на новую модель синхронизации, предоставляемую Microsoft Sync Framework. Сведения см. в разделе [Центр разработчиков Microsoft Sync Framework](https://msdn.microsoft.com/sync/default)|
|Платформа MVC ("модель-представление-контроллер")|Visual Studio 2010 с пакетом обновления 1 (SP1) поддерживает только MVC 2 и MVC 3, Visual Studio 2012 — только MVC 3 и MVC 4, а Visual Studio 2013 — только MVC 4. Сведения об автоматическом обновлении MVC 2 до MCV 3 см. в разделе [Средство обновления приложения MVC 3 ASP.NET](https://aspnet.codeplex.com/releases/view/59008). Сведения об обновлении MVC 2 до MVC 3 вручную см. в разделе [Обновление проекта ASP.NET MVC 2 до обновления инструментов ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Сведения об обновлении MVC3 до MVC 4 вручную см. в разделе [Обновление проекта ASP.NET MVC 3 до ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes). Если проект ориентирован на платформу .NET Framework 3.5 с пакетом обновления 1 (SP1), необходимо переориентировать его на .NET Framework 4.|
|Моделирование|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).<br /><br /> Когда сервер Team Foundation собирает проект моделирования, он пытается проверить слои в проекте. В Visual Studio 2013 Team Foundation Build не может проверить слои проекта моделирования, созданного в Visual Studio 2010 с пакетом обновления 1 (SP1). Однако в Visual Studio 2010 с пакетом обновления 1 (SP1) Team Foundation Build поддерживает проверку слоев в проекте моделирования, созданном в Visual Studio 2013.|
|Отладка MPI-кластера|Если на компьютерах с Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1) установлена одна и та же версия среды выполнения или инструментов, этот проект можно открывать во всех трех версиях.|
|Пакет установки (VDPROJ)|Этот проект невозможно открыть в Visual Studio 2013, так как эта версия не поддерживает данный тип проекта. Рекомендуется использовать InstallShield Limited Edition для Visual Studio (ISLE), бесплатное решение для развертывания, которое поддерживает большинство сред выполнения приложений и платформ Windows. Также можно использовать ISLE для импорта данных и параметров из проектов установщиков Visual Studio. .|
|Office 2007 VSTO|При обновлении проекта для Office 2013 и .NET Framework 4 можно открыть этот проект в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Office 2010 VSTO|Если проект предназначен для платформы .NET Framework 4, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Все остальные проекты требуют одностороннего обновления.|
|Полнофункциональные интернет-приложения|При обновлении проекта его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|SharePoint 2007|Этот проект невозможно открыть в Visual Studio 2013. Однако если необходимо вручную обновить проект до SharePoint 2010, можно открыть его в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Дополнительные сведения об обновлении SharePoint 2007 см. в статьях [Миграция с SharePoint 2007 в SharePoint 2010 для ИТ-специалистов](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) и [Поиск в корпоративной среде SharePoint](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|SketchFlow|Если разрешить Visual Studio обновить проект до WPF 4.5/Silverlight 5, его можно будет открыть в Visual Studio 2012 and Visual Studio 2013.|
|База данных [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|Проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Если имеется файл базы данных, (MDF), созданный в более ранней версии SQL Server, необходимо обновить ее в [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] , прежде чем его можно будет использовать с базой данных LocalDB SQL Server Express, но база данных больше не будет совместима с предыдущими версиями SQL Server. Если не выполнить обновление, можно продолжать работать с базой данных в Visual Studio 2013, установив на том же компьютере [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]. Дополнительные сведения см. в статье [Обновление MDF-файлов](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Если на компьютерах с Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1) установлен выпуск Express [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)], проект можно открывать во всех трех версиях.|
|Проект отчетов SQL Server|Проект можно открыть в Visual Studio 2013 и Visual Studio 2012. Если используется только локальный режим (то есть без подключения к SQL Server), у пользователя нет возможности использования элементов управления, связанных со средством просмотра в [!INCLUDE[vs2010](../includes/vs2010-md.md)], во время разработки, однако сам проект функционирует корректно во время выполнения. **Внимание!** При добавлении возможности, которая присутствует только в Visual Studio 2013, схема отчета обновляется автоматически и возможность открывать проект в Visual Studio 2012 пропадает.|
|Модульные тесты|Чтобы открывать тесты, созданные в любой из этих версий, вы можете использовать [!INCLUDE[TCMext](../includes/tcmext-md.md)] в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Visual C++|С помощью Visual Studio 2013 можно открыть проект C++, который был создан в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1). Если требуется использовать среду сборки Visual Studio 2013 для сборки проекта, созданного в Visual Studio 2012, нужно, чтобы на компьютере были установлены обе версии Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) и [Руководство по переносу и обновлению Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 web|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|База данных Visual Studio 2010 (DBPROJ)|При преобразовании проекта в проект базы данных SQL Server Data Tools его можно открыть в Visual Studio 2013. Однако Visual Studio 2013 не поддерживает следующие артефакты:<br /><br /> — модульные тесты;<br />— планы создания данных;<br />— файлы сравнения данных;<br />— пользовательские расширения правил для анализа статического кода;<br />— server.sqlsettings;<br />— SQLCMD-файлы;<br />— пользовательские расширения развертывания;<br />— частичные проекты (.files).<br /><br /> Если установить SQL Server Data Tools, можно открыть проект в Visual Studio 2010 с пакетом обновления 1 (SP1) после преобразования. Дополнительные сведения см. в разделе [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Визуальные инструменты для баз данных в Visual Studio 2010|Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Visual Studio Lab Management|[!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1) можно использовать для открытия сред, которые были созданы в какой-либо из этих версий. Однако версия Microsoft Test Manager должна соответствовать версии Team Foundation Server, чтобы можно было создавать среды.|
|Макрос Visual Studio|Этот проект невозможно открыть в Visual Studio 2013, так как эта версия не поддерживает данный тип проектов.|
|SDK для Visual Studio/VSIX|После обновления проекта пакета SDK для Visual Studio до Visual Studio 2013 его невозможно будет открыть в Visual Studio 2012. Дополнительные сведения см. в разделе [Практическое руководство. перенести проекты расширяемости в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Инструменты Microsoft Azure для Visual Studio|При использовании инструментов Microsoft Azure для Visual Studio версии 2.1 проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). Для проектов, ориентированных на более ранние версии, если разрешить Visual Studio обновить проект до версии 2.1, можно будет открыть его в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Windows Communication Foundation, Windows Presentation Foundation|Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Windows Mobile|Этот проект невозможно открыть в Visual Studio 2013, так как эта версия не поддерживает данный тип проектов.|
|Windows Phone 7.1|Если разрешить Visual Studio обновить проект до Windows Phone 8.0, его можно будет открыть в Visual Studio 2012 и Visual Studio 2013.|
|Другой|Проекты большинства других типов можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Веб-сайты FrontPage|Этот проект невозможно открыть в Visual Studio 2013, так как эта версия не поддерживает данный тип проектов.|
|Переносимая библиотека классов|Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2013, Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).<br /><br /> — Проекты, ориентированные на Silverlight 4, ориентированы и на Silverlight 5.<br />— Проекты для Windows Phone 7.0 или Windows Phone 7.5 ориентированы и на Windows Phone 8.<br />— Проекты, ориентированные на Xbox 360, более не будут ориентированы на Xbox 360.|
|Проекты Azure, такие как проекты облачных служб (с расширением CCPROJ) и проекты диспетчера ресурсов Azure (проекты облачного развертывания) с расширением DEPLOYPROJ|Для открытия этих типов проектов сначала установите [пакет Azure SDK для .NET](https://azure.microsoft.com/downloads/), а затем откройте соответствующий проект.|

## <a name="troubleshooting-project-compatibility-issues"></a>Устранение проблем совместимости проектов
 Ниже описаны некоторые меры, которые можно принять, если проект не открывается в Visual Studio 2015 или Visual Studio 2013.

- При попытке открыть проект, который не поддерживается в Visual Studio 2015 или Visual Studio 2013 и для которого не установлена соответствующая версия Visual Studio, может появляться сообщение о том, что тип проекта не поддерживается, а тип проекта может быть указан в диалоговом окне **Анализ изменений проекта и решения** в разделе **Unsupported projects** (Неподдерживаемые проекты). Для устранения этой проблемы откройте страницу программ и компонентов на **панели управления**Windows, выберите **Visual Studio**, а затем выберите **Изменить**и **Восстановить**. Затем можно будет установить отсутствующую версию.

- При попытке открыть проект для классического приложения в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] возникает ошибка и отображается одно из следующих сообщений: "Этот выпуск Visual Studio поддерживает только приложения [!INCLUDE[win81](../includes/win81-md.md)]" или "Этот проект несовместим с текущим выпуском Visual Studio". Версия [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] предназначена для разработки, тестирования и развертывания приложений Магазина Windows, созданных для Windows 8.1. Чтобы открыть проект классического приложения, необходимо использовать выпуск Visual Studio, поддерживающий этот тип проекта.

   Дополнительные сведения о выпусках Visual Studio см. в описании [продуктов Microsoft Visual Studio](https://visualstudio.microsoft.com/products/).

- При попытке открыть проект приложения для Магазина Windows в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, возникает ошибка. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop нельзя использовать для создания приложений для Магазина Windows. Если требуется создавать приложения для Магазина Windows, можно также установить [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. А для разработки приложений для всех платформ Microsoft и Интернета попробуйте Visual Studio Professional 2013.

- Если для проекта требуются функции, присутствующие только в Visual Studio 2013, его невозможно открыть в более ранней версии.

- Если используется Visual Studio 2012 и необходимо открыть проект, созданный в Visual Studio 2013, возможно, удастся настроить систему проектов, чтобы она включала функции Visual Studio 2013. Дополнительные сведения см. в статье [Обеспечение поддержки версий в пользовательских проектах](../misc/making-custom-projects-version-aware.md).

  Дополнительные сведения об устранении неполадок см. в статье базы знаний [Совместимость Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) .

## <a name="file"></a> Файлы

В следующем списке указано, поддерживает ли Visual Studio 2013 тот или иной тип файлов, можно ли открыть файл в Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1) и нужно ли изменить его, чтобы обеспечить совместимость.

|Тип файлов|Совместимость|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (XML-файлы)|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Схемы неструктурированных файлов BizTalk|Эти схемы можно добавлять в проект BizTalk 2013 в Visual Studio 2013. Для использования Visual Studio 2013 с проектами BizTalk 2010, содержащими схемы неструктурированных файлов, установите BizTalk 2013 на компьютере с Visual Studio 2013. При первом открытии проекта BizTalk 2010 он автоматически обновляется до BizTalk 2013 или системы проектов Visual Studio 2013.|
|Файлы определений клиентских отчетов (RDLC)|Эти файлы можно открывать в Visual Studio 2013, а схема автоматически обновляется при добавлении функций и элементов управления Visual Studio 2013.|
|Наборы правил анализа кода|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы пакетов приложений уровня данных|Эти файлы можно открывать в Visual Studio 2013, если они имеют версию 2.0 или 2.5.|
|Файлы дампов отладчика|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы диаграмм DGML|Эти файлы можно открывать в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1), не изменяя файлы.|
|Файлы моделей данных с использованием сущностей (EDMX)|В Visual Studio 2013 можно открыть файл EDMX, который предназначен для .NET Framework 4.5 или .NET Framework 4, не изменяя этот файл.|
|Файлы отчетов профилировщика|Файлы отчетов профилировщика (VSP, VSPS, PSESS и VSPF) можно открывать в Visual Studio 2012 и Visual Studio 2013. VSPX-файлы невозможно открывать в Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файл решения (SUO)|С помощью Visual Studio 2013 можно открыть файл решения, который был создан в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).|
|SQL Server Compact Edition|Visual Studio 2013 не поддерживает SQL Server Compact Edition.|
|SQLX-файлы|Чтобы открыть эти файлы в Visual Studio 2013, необходимо выполнить одностороннее обновление, развернуть SQLX-файл в целевой версии Visual Studio, а затем пересобрать файл в формате DACPAC.|
|Файлы журналов IntelliTrace из [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Эти файлы можно открыть в Visual Studio 2012, Visual Studio 2013 и Visual Studio 2010 с пакетом обновления 1 (SP1).|
|Файлы анализатора памяти JavaScript (DIAGSESSION)|Файлы, созданные в более старых версиях Visual Studio, можно просматривать в Visual Studio 2013. Однако в зависимости от собранных данных файлы, созданные в Visual Studio 2013, могут не открыться в Visual Studio 2012 или Visual Studio 2010 с пакетом обновления 1 (SP1).|

## <a name="integration"></a> Активы интеграции

Проблемы совместимости могут возникнуть при использовании клиентов и серверов из разных версий Visual Studio Team Foundation Server.

|Тип интеграции|Совместимость|
|-------------------------|-------------------|
|"Проверка кода" и "Моя работа"|Функции "Проверка кода" и "Моя работа" не будут работать при подключении клиента [!INCLUDE[esprfound](../includes/esprfound-md.md)] к [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|64-разрядную среду, такую как MSBuild или [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] , невозможно использовать для сборки приложений [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , создаваемых в [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>См. также

- [Обеспечение поддержки версий в пользовательских проектах](../misc/making-custom-projects-version-aware.md)
