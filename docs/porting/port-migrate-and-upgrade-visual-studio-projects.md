---
title: "Перенос, миграция и обновление проектов Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 7/24/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e48ebcafaca37505dbcc92bce682d0c6169004e1
ms.openlocfilehash: 8124ac4629b337faeb88ce40b1e162d7ce012e7f
ms.contentlocale: ru-ru
ms.lasthandoff: 07/26/2017

---

# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Перенос, миграция и обновление проектов Visual Studio

Как правило, каждая новая версия Visual Studio поддерживает большую часть типов проектов, файлов и других ресурсов предыдущих выпусков. С ними можно работать, как обычно, и при условии, что вы не зависите от новых функций, Visual Studio сохраняет обратную совместимость с предыдущими версиями Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012. (См. [заметки о выпуске](https://www.visualstudio.com/vs/release-notes/), чтобы узнать, какие функции к какой версии относятся.)

Но поддержка некоторых типов со временем меняется. Более новая версия Visual Studio может больше не поддерживать некоторые типы или же может потребоваться перенести и обновить их так, чтобы они не являлись обратно совместимыми. Текущее состояние проблем с миграцией см. на [сайте сообщества разработчиков Visual Studio](https://developercommunity.visualstudio.com).

> [!Important]
> Этот раздел содержит только сведения о типах проектов в Visual Studio 2017, связанных с миграцией. Здесь не указаны поддерживаемые типы проектов, не имеющие проблем с миграцией. Этот список находится на странице [целевой платформы и совместимости](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs). Обратите внимание, что некоторые типы проектов больше не поддерживаются в Visual Studio 2017 и поэтому не могут быть перенесены.

> [!Important]
> Для открытия отдельных типов проектов требуется добавить соответствующие рабочие нагрузки в установщике Visual Studio. При отсутствии установленной рабочей нагрузки Visual Studio сообщает о неизвестном или несовместимом типе проекта. В этом случае проверьте параметры установки и повторите попытку. Просмотрите раздел [целевой платформы и совместимости](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs) для получения сведений о поддержке проектов в Visual Studio 2017.

## <a name="projects"></a>Проекты

В следующем списке описывается поддержка проектов Visual Studio 2017, созданных в более ранних версиях.

Если здесь отсутствует проект или тип файла, который должен быть, проверьте [версию Visual Studio 2015 в этом разделе](https://msdn.microsoft.com/library/hh266747.aspx) и запишите ее в комментариях ниже.

| Тип проекта | Поддержка |
| --- | --- |
| Проекты .NET Core (XPROJ) | В проектах, созданных в Visual Studio 2015, использовались предварительные версии средств, включающие XPROJ-файл проекта. При открытии XPROJ-файла в Visual Studio 2017 вам будет предложено перенести файл в формат CSPROJ (создается резервная копия XPROJ-файла). Этот формат CSPROJ для проектов .NET Core не поддерживается в VS 2015 и более ранних версиях.  Формат XPROJ не поддерживается в Visual Studio 2017, за исключением переноса в формат CSPROJ. Дополнительные сведения см. в статье [Перенос проектов .NET Core в формат .csproj](https://docs.microsoft.com/dotnet/core/migration/#visual-studio-2017).|
| Веб-приложение ASP.NET и веб-приложения ASP.NET Core с включенной службой Application Insights | В Visual Studio сведения о ресурсах хранятся в реестре для каждого экземпляра пользователя. Это действует в случае, если пользователь не открыл проект и хочет найти данные Azure Application Insights. Расположение реестра в Visual Studio 2015 отличается от расположения реестра в Visual Studio 2017, поэтому конфликты отсутствуют.<br/><br/>Когда пользователь создает веб-приложение ASP.NET или веб-приложение ASP.NET Core, ресурс сохраняется в SUO-файл. Пользователь может открыть проект в Visual Studio 2015 или 2017 и сведения о ресурсе будут использоваться в обеих версиях до тех пор, пока Visual Studio поддерживает проекты и решения, используемые в обеих версиях. Пользователям потребуется пройти проверку подлинности один раз в каждой версии продукта. Например, если проект создается в Visual Studio 2015 и открывается в Visual Studio 2017, пользователю потребуется пройти проверку подлинности в Visual Studio 2017 г. |
| Веб-форма или форма Windows C#/Visual Basic | Проект можно открыть в Visual Studio 2017 и Visual Studio 2015. |
| Проекты модульных тестов базы данных (CSPROJ, VBPROJ)    | Старые проекты модульных тестов данных будут загружены в Visual Studio 2017, но они будут использовать GAC-версию зависимостей. Чтобы обновить проект модульного теста для использования последних зависимостей, щелкните проект правой кнопкой мыши в обозревателе решений и выберите **Преобразовать в проект модульного тестирования SQL Server**. |
| F# | В Visual Studio 2017 можно открывать проекты, созданные в Visual Studio 2013 и 2015. Чтобы включить функции Visual Studio 2017 в этих проектах, откройте окно свойств проекта, и измените целевой объект fsharp.core на F# 4.1. Обратите внимание, что вариант **Поддержка языка F #** в установщике Visual Studio не выбран по умолчанию с рабочими нагрузками .NET; необходимо включить его, выбрав соответствующий параметр для рабочей нагрузки или выбрав его на вкладке **Отдельные компоненты** в разделе **Действия разработки**. |
| InstallShield<br/>Установка MSI | Проекты установщика, созданные в Visual Studio 2010, можно открыть в более поздних версиях с помощью [расширения проектов установщика Visual Studio](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects). Также см. сведения о [расширении набора инструментов WiX для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). InstallShield Limited Edition больше не входит в состав Visual Studio. Уточните доступность этого решения для Visual Studio 2017 у компании [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio). |
| LightSwitch | LightSwitch больше не поддерживается в Visual Studio 2017. Проекты, созданные в Visual Studio 2012 и более ранних версиях и открытые в Visual Studio 2013 или Visual Studio 2015, будут обновлены и затем могут быть открыты только в Visual Studio 2013 или Visual Studio 2015. |
| Инструменты Microsoft Azure для Visual Studio | Для открытия этих типов проектов сначала установите [пакет Azure SDK для .NET](http://azure.microsoft.com/downloads/), а затем откройте соответствующий проект. При необходимости проект будет обновлен. |
| Платформа MVC ("модель-представление-контроллер") (ASP.NET MVC) | Поддержка версий MVC и Visual Studio:<ul><li>Visual Studio 2010 с пакетом обновления 1 (SP1) поддерживает MVC 2 и MVC 3. Поддержка MVC 4 добавляется с помощью [скачивания ASP.NET 4 MVC 4 для Visual Studio 2010 с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=30683).</li><li>Visual Studio 2012 поддерживает только MVC 3 и MVC 4.</li><li>Visual Studio 2013 поддерживает только MVC 4 и MVC 5</li><li>Visual Studio 2017 и Visual Studio 2015 поддерживают MVC 4 (можно открывать существующие проекты, но не создавать новые) и MVC 5.</li></ul><br/><br/>Обновление версий MVC:<ul><li>Сведения об автоматическом обновлении MVC 2 до MCV 3 см. в разделе [Средство обновления приложения MVC 3 ASP.NET](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Сведения об обновлении MVC 2 до MVC 3 вручную см. в разделе [Обновление проекта ASP.NET MVC 2 до обновления инструментов ASP.NET MVC 3](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Сведения об обновлении MVC3 до MVC 4 вручную см. в разделе [Обновление проекта ASP.NET MVC 3 до ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Если проект ориентирован на платформу .NET Framework 3.5 с пакетом обновления 1 (SP1), необходимо переориентировать его на .NET Framework 4.</li><li>Сведения об обновлении MVC 4 до MVC 5 вручную см. в разделе [Обновление проекта ASP.NET MVC 4 и веб-API до ASP.NET MVC 5 и веб-API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2).</li></ul> |
| Моделирование | Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2015, Visual Studio 2013 или Visual Studio 2012.<br/><br/>Формат проекта моделирования не изменился в версиях с Visual Studio 2015 по Visual Studio 2017, и проект можно открыть и изменить в любой версии. Но в Visual Studio 2017 существуют различия в поведении.<ul><li>Теперь проекты моделирования называются в меню и шаблонах проектами проверки зависимостей.</li><li>UML-схемы больше не поддерживаются в Visual Studio 2017. UML-файлы указываются в обозревателе решений как и ранее, но открываются как XML-файлы. Для просмотра, создания или изменения UML-схем следует использовать Visual Studio 2015.</li><li>В Visual Studio 2017 проверка архитектурных зависимостей больше не выполняется при сборке проекта моделирования. Вместо этого проверка осуществляется при сборке каждого проекта кода. Это изменение не влияет на проект моделирования, но необходимо внести изменения в проверяемые проекты кода. Visual Studio 2017 автоматически вносит необходимые изменения в проекты кода ([дополнительные сведения](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| Установка MSI (.vdproj) | См. выше раздел "Проекты InstallShield". | 
| Office 2007 VSTO | Требует одностороннего обновления до Visual Studio 2017. |
| Office 2010 VSTO | Если проект предназначен для платформы .NET Framework 4, его можно открыть в Visual Studio 2010 с пакетом обновления 1 (SP1). Все остальные проекты требуют одностороннего обновления. |
| SharePoint 2010 | Когда вы откроете проект SharePoint в Visual Studio 2017, он обновляется до SharePoint 2013 или SharePoint 2016. Для этого обновления в Visual Studio 2017 должна быть установлена рабочая нагрузка "Разработка классических приложений .NET".<br/><br/>Дополнительные сведения об обновлении проектов SharePoint см. в статьях [Обновление до SharePoint 2013](https://technet.microsoft.com/library/cc303420.aspx), [Обновление рабочего процесса в SharePoint Server 2013](https://technet.microsoft.com/library/dn133867.aspx) и [Создание фермы SharePoint Server 2016 для обновления с переподключением баз данных](https://technet.microsoft.com/library/cc263026(v=office.16).aspx). |
| SharePoint 2016 | Проекты надстройки SharePoint, созданные в предварительной версии Office Developer Tools 2, невозможно открыть в Visual Studio 2017. Чтобы обойти это ограничение, следует указать в файле `.csproj` или `.vbproj` значение 12.0 для параметра `MinimumVisualStudioVersion` и значение 12.2 для параметра `MinimumOfficeToolsVersion`. |
| Silverlight | Проекты Silverlight не поддерживаются в Visual Studio 2017. Для поддержки приложений Silverlight продолжайте использовать Visual Studio 2015. |
| Службы SQL Server Reporting Services и службы SQL Server Analysis Services (SSRS, SSDT, SSAS, MSAS) | Поддержка этих типов проектов обеспечивается двумя расширениями из коллекции Visual Studio: [проекты моделирования Microsoft Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects) и [проекты Microsoft Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio). Поддержка SSDT также включена в рабочую нагрузку хранения и обработки данных в Visual Studio 2017. |
| Службы интеграции SQL Server (SSIS) | В Visual Studio 2017 эти службы пока не поддерживаются. О начале поддержки будет объявлено в [блоге SQL Server Integration Services](https://blogs.msdn.microsoft.com/ssis/). Сейчас для работы со службами SSIS мы рекомендуем продолжать использовать Visual Studio 2015. |
| Visual C++ | Visual Studio 2017 можно использовать как есть для открытия решений и проектов, созданных в Visual Studio 2015, но для проектов, созданных в более ранних версиях Visual Studio, может потребоваться обновить проект или переназначить более новый набор инструментов. Дополнительные сведения см. в статье [Руководство по переносу и обновлению Visual C++](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide). |
| Расширяемость Visual Studio/VSIX | Проекты с минимальной версией 14.0 или меньше будут обновлены до минимальной версии 15.0, что не позволяет открывать проекты в более ранних версиях Visual Studio. Чтобы открыть проект в более ранних версиях, задайте `$(VisualStudioVersion)` в качестве значения минимальной версии. См. также [Практическое руководство. Перенос проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Microsoft Test Manager или Visual Studio 2010 с пакетом обновления 1 (SP1) можно использовать для открытия сред, которые были созданы в какой-либо из этих версий. Но версия Microsoft Test Manager должна соответствовать версии Visual Studio 2010 с пакетом обновления 1 (SP1), чтобы можно было создавать среды. |
| Средства Visual Studio для Apache Cordova |Этот проект можно открыть в Visual Studio 2017, но он не является обратно совместимым. После открытия проекта в Visual Studio 2015 будет предложено разрешить внесение изменений в проект. Это позволит обновить проект, чтобы вместо файла `taco.json` использовать набор инструментов для управления версиями библиотеки Cordova, платформами и подключаемыми модулями, а также зависимостями узлов или npm. Дополнительные сведения см. в [руководстве по миграции](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/first-steps/migrate-from-visual-studio-2015). |
| Windows Communication Foundation, Windows Workflow Foundation | Этот проект можно открыть в Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012. |
| Windows Presentation Foundation | Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). |
| Приложения для Магазина Windows и Windows Phone | В Visual Studio 2017 не поддерживаются проекты для Магазина Windows 8.1 и Магазина Windows 8.0 и для Windows Phone 8.1 и Windows Phone 8.0. Для поддержки этих приложений продолжайте использовать Visual Studio 2015. Для поддержки проектов Windows Phone 7.x используйте Visual Studio 2012. |

