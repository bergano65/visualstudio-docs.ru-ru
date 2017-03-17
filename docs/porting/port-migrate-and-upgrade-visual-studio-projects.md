---
title: "Перенос, миграция и обновление проектов Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 2/27/2017
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
ms.sourcegitcommit: dac3cb1d7767c2ff76ac25f6a486ad30a8d54831
ms.openlocfilehash: 6b61cbc8460266ac305b12bf14f92d7445bfc900
ms.lasthandoff: 03/03/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Перенос, миграция и обновление проектов Visual Studio

Как правило, каждая новая версия Visual Studio поддерживает большую часть типов проектов, файлов и других ресурсов предыдущих выпусков. С ними можно работать, как обычно, и при условии, что вы не зависите от новых функций, Visual Studio сохраняет обратную совместимость с предыдущими версиями Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012. (См. [заметки о выпуске](https://www.visualstudio.com/vs/release-notes/), чтобы узнать, какие функции к какой версии относятся.)

Но поддержка некоторых типов со временем меняется. Более новая версия Visual Studio может больше не поддерживать некоторые типы или же может потребоваться перенести и обновить их так, чтобы они не являлись обратно совместимыми. В этом разделе содержатся сведения о затронутых типах проектов в Visual Studio 2017. Список поддерживаемых типов для Visual Studio 2017 можно найти в разделе [Целевая платформа и совместимость](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs).

> [!Note]
> Для открытия определенных типов проектов требуется добавить соответствующую рабочую нагрузку с помощью установщика Visual Studio.


## <a name="projects"></a>Проекты

В следующем списке описывается поддержка проектов Visual Studio 2017, созданных в более ранних версиях. Если здесь отсутствует проект или тип файла, который должен быть, проверьте [версию Visual Studio 2015 в этом разделе](https://msdn.microsoft.com/library/hh266747.aspx) и запишите ее в комментариях ниже.

| Тип проекта | Поддержка |
| --- | --- |
| Проекты .NET Core (XPROJ) | В проектах, созданных в Visual Studio 2015, использовались предварительные версии средств, включающие XPROJ-файл проекта. При открытии XPROJ-файла в Visual Studio 2017 вам будет предложено перенести файл в формат CSPROJ (создается резервная копия XPROJ-файла). Этот формат CSPROJ для проектов .NET Core не поддерживается в VS 2015 и более ранних версиях.  Формат XPROJ не поддерживается в Visual Studio 2017, за исключением переноса в формат CSPROJ. |
| Веб-приложение ASP.NET и веб-приложения ASP.NET Core с включенной службой Application Insights | В Visual Studio сведения о ресурсах хранятся в реестре для каждого экземпляра пользователя. Это действует в случае, если пользователь не открыл проект и хочет найти данные Azure Application Insights. Расположение реестра в Visual Studio 2015 отличается от расположения реестра в Visual Studio 2017, поэтому конфликты отсутствуют.<br/><br/>Когда пользователь создает веб-приложение ASP.NET или веб-приложение ASP.NET Core, ресурс сохраняется в SUO-файл. Пользователь может открыть проект в Visual Studio 2015 или 2017 и сведения о ресурсе будут использоваться в обеих версиях до тех пор, пока Visual Studio поддерживает проекты и решения, используемые в обеих версиях. Пользователям потребуется пройти проверку подлинности один раз в каждой версии продукта. Например, если проект создается в Visual Studio 2015 и открывается в Visual Studio 2017, пользователю потребуется пройти проверку подлинности в Visual Studio 2017 г. |
| Веб-форма или форма Windows C#/Visual Basic | Проект можно открыть в Visual Studio 2017 и Visual Studio 2015. |
| Проекты модульных тестов базы данных (CSPROJ, VBPROJ)    | Старые проекты модульных тестов данных будут загружены в Visual Studio 2017, но они будут использовать GAC-версию зависимостей. Чтобы обновить проект модульного теста для использования последних зависимостей, щелкните проект правой кнопкой мыши в обозревателе решений и выберите **Преобразовать в проект модульного тестирования SQL Server**. |
| F# | В Visual Studio 2017 можно открывать проекты, созданные в Visual Studio 2013 и 2015. Чтобы включить функции Visual Studio 2017 в этих проектах, откройте окно свойств проекта, и измените целевой объект fsharp.core на F# 4.1. |
| LightSwitch | LightSwitch больше не поддерживается в Visual Studio 2017. Проекты, созданные в Visual Studio 2012 и более ранних версиях и открытые в Visual Studio 2013 или Visual Studio 2015, будут обновлены и затем могут быть открыты только в Visual Studio 2013 или Visual Studio 2015. |
| Инструменты Microsoft Azure для Visual Studio | Для открытия этих типов проектов сначала установите [пакет Azure SDK для .NET](http://azure.microsoft.com/en-us/downloads/), а затем откройте соответствующий проект. При необходимости проект будет обновлен. |
| Платформа MVC ("модель-представление-контроллер") (ASP.NET MVC) | Поддержка версий MVC и Visual Studio:<ul><li>Visual Studio 2010 с пакетом обновления 1 (SP1) поддерживает MVC 2 и MVC 3. Поддержка MVC 4 добавляется с помощью [скачивания ASP.NET 4 MVC 4 для Visual Studio 2010 с пакетом обновления 1 (SP1)](https://www.microsoft.com/en-us/download/details.aspx?id=30683).</li><li>Visual Studio 2012 поддерживает только MVC 3 и MVC 4.</li><li>Visual Studio 2013 поддерживает только MVC 4 и MVC 5</li><li>Visual Studio 2017 и Visual Studio 2015 поддерживают MVC 4 (можно открывать существующие проекты, но не создавать новые) и MVC 5.</li></ul><br/><br/>Обновление версий MVC:<ul><li>Сведения об автоматическом обновлении MVC 2 до MCV 3 см. в разделе [Средство обновления приложения MVC 3 ASP.NET](http://go.microsoft.com/fwlink/?LinkID=238178).</li><li>Сведения об обновлении MVC 2 до MVC 3 вручную см. в разделе [Обновление проекта ASP.NET MVC 2 до обновления инструментов ASP.NET MVC 3](http://go.microsoft.com/fwlink/?linkid=238178).</li><li>Сведения об обновлении MVC3 до MVC 4 вручную см. в разделе [Обновление проекта ASP.NET MVC 3 до ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes). Если проект ориентирован на платформу .NET Framework 3.5 с пакетом обновления 1 (SP1), необходимо переориентировать его на .NET Framework 4.</li><li>Сведения об обновлении MVC 4 до MVC 5 вручную см. в разделе [Обновление проекта ASP.NET MVC 4 и веб-API до ASP.NET MVC 5 и веб-API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2).</li></ul> |
| Моделирование | Если разрешить автоматическое обновление проекта в Visual Studio, его можно открыть в Visual Studio 2015, Visual Studio 2013 или Visual Studio 2012.<br/><br/>Формат проекта моделирования не изменился в версиях с Visual Studio 2015 по Visual Studio 2017, и проект можно открыть и изменить в любой версии. Но в Visual Studio 2017 существуют различия в поведении.<ul><li>Теперь проекты моделирования называются в меню и шаблонах проектами проверки зависимостей.</li><li>UML-схемы больше не поддерживаются в Visual Studio 2017. UML-файлы указываются в обозревателе решений как и ранее, но открываются как XML-файлы. Для просмотра, создания или изменения UML-схем следует использовать Visual Studio 2015.</li><li>В Visual Studio 2017 проверка архитектурных зависимостей больше не выполняется при сборке проекта моделирования. Вместо этого проверка осуществляется при сборке каждого проекта кода. Это изменение не влияет на проект моделирования, но необходимо внести изменения в проверяемые проекты кода. Visual Studio 2017 автоматически вносит необходимые изменения в проекты кода ([дополнительные сведения](http://go.microsoft.com/fwlink/?LinkId=827800)).</li></ul> |
| Silverlight | Проекты Silverlight не поддерживаются в Visual Studio 2017. Для поддержки приложений Silverlight продолжайте использовать Visual Studio 2015. |
| Visual C++ | Visual Studio 2017 можно использовать как есть для открытия решений и проектов, созданных в Visual Studio 2015, но для проектов, созданных в более ранних версиях Visual Studio, может потребоваться обновить проект или переназначить более новый набор инструментов. Дополнительные сведения см. в разделах [Практическое руководство. Обновление проектов Visual C++ до Visual Studio 2015](https://msdn.microsoft.com/en-us/library/hh690665.aspx) и [Руководство по переносу и обновлению Visual C++](https://msdn.microsoft.com/en-us/library/dn986839.aspx). |
| Расширяемость Visual Studio/VSIX | Проекты с минимальной версией 14.0 или меньше будут обновлены до минимальной версии 15.0, что не позволяет открывать проекты в более ранних версиях Visual Studio. Чтобы открыть проект в более ранних версиях, задайте `$(VisualStudioVersion)` в качестве значения минимальной версии. См. также [Практическое руководство. Перенос проектов расширяемости в Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md). |
| Visual Studio Lab Management | Microsoft Test Manager или Visual Studio 2010 с пакетом обновления 1 (SP1) можно использовать для открытия сред, которые были созданы в какой-либо из этих версий. Но версия Microsoft Test Manager должна соответствовать версии Visual Studio 2010 с пакетом обновления 1 (SP1), чтобы можно было создавать среды. |
| Средства Visual Studio для Apache Cordova |Этот проект можно открыть в Visual Studio 2017, но он не является обратно совместимым. После открытия проекта в Visual Studio 2015 будет предложено разрешить внесение изменений в проект. Это позволит обновить проект, чтобы вместо файла `taco.json` использовать набор инструментов для управления версиями библиотеки Cordova, платформами и подключаемыми модулями, а также зависимостями узлов или npm. Дополнительные сведения см. в [руководстве по миграции](http://taco.visualstudio.com/docs/vs-taco-2017-migration/). |
| Windows Communication Foundation, Windows Workflow Foundation | Этот проект можно открыть в Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 и Visual Studio 2012. |
| Windows Presentation Foundation | Этот проект можно открыть в Visual Studio 2013, Visual Studio 2012 и Visual Studio 2010 с пакетом обновления 1 (SP1). |
| Приложения для Магазина Windows и Windows Phone | В Visual Studio 2017 не поддерживаются проекты для Магазина Windows 8.1 и Магазина Windows 8.0 и для Windows Phone 8.1 и Windows Phone 8.0. Для поддержки этих приложений продолжайте использовать Visual Studio 2015. Для поддержки проектов Windows Phone 7.x используйте Visual Studio 2012. |
