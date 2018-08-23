---
title: Установка и использование Visual Studio и служб Azure, расположенных за брандмауэром или прокси-сервером | Документация Майкрософт
description: Узнайте, какие URL-адреса доменов, порты и протоколы может потребоваться внести в список разрешений или открыть, если в организации применяется брандмауэр или прокси-сервер.
ms.custom: ''
ms.date: 07/10/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 911bedf391a37f64ba1f71179e2a3060be152842
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978441"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Установка и использование Visual Studio и служб Azure, расположенных за брандмауэром или прокси-сервером

Если вы или ваша организация используете средства обеспечения безопасности, например брандмауэр или прокси-сервер, значит есть URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы обеспечить оптимальные установку и использование Visual Studio и служб Azure.

* **[Установка Visual Studio](#install-visual-studio)**. Таблицы в этом разделе содержат URL-адреса доменов, которые нужно добавить в список разрешений, чтобы получить доступ ко всем необходимым компонентам и рабочим нагрузкам.

* **[Использование Visual Studio и служб Azure](#use-visual-studio-and-azure-services)**. Таблица в этом разделе содержит URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы получить доступ ко всем необходимым компонентам и службам.

## <a name="install-visual-studio"></a>Установка Visual Studio

### <a name="urls-to-whitelist"></a>URL-адреса для добавления в список разрешений

С учетом того, что Visual Studio Installer скачивает файлы из различных доменов и их серверов загрузки, ниже приведены URL-адреса доменов, которые нужно добавить в список разрешений как доверенные с помощью пользовательского интерфейса или скриптов развертывания.

#### <a name="microsoft-domains"></a>Домены Майкрософт

| Домен | Цель |
| ------ | ------- |
| go.microsoft.com | Настройка разрешения URL-адресов |
| aka.ms | Настройка разрешения URL-адресов |
| download.visualstudio.microsoft.com | Настройка расположения для скачивания пакетов |
| download.microsoft.com | Настройка расположения для скачивания пакетов |
| download.visualstudio.com | Настройка расположения для скачивания пакетов |
| dl.xamarin.com | Настройка расположения для скачивания пакетов |
| visualstudiogallery.msdn.microsoft.com | Расположение для скачивания расширений Visual Studio |
| visualstudio.microsoft.com | Расположение документации |
| docs.microsoft.com | Расположение документации |
| msdn.microsoft.com | Расположение документации |
| www.microsoft.com | Расположение документации |
| *.windows.net | Расположение входа |
| *.microsoftonline.com | Расположение входа |
| *.live.com | Расположение входа |
|  |  | |

#### <a name="non-microsoft-domains"></a>Сторонние домены

| Домен | Устанавливает эти рабочие нагрузки |
| ------ | ------- |
| archive.apache.org |  Разработка мобильных приложений с помощью JavaScript (Cordova) |
| cocos2d-x.org | Разработка игр с помощью C++ (Cocos) |
| download.epicgames.com | Разработка игр с помощью C++ (Unreal Engine) |
| download.oracle.com | Разработка мобильных приложений с помощью JavaScript (пакет SDK для Java) <br /><br />Разработка мобильных приложений с помощью .NET (пакет SDK для Java) |
| download.unity3d.com | Разработка игр с помощью Unity (Unity) |
| netstorage.unity3d.com | Разработка игр с помощью Unity (Unity) |
| dl.google.com | Разработка мобильных приложений с помощью JavaScript (пакеты SDK и NDK для Android, эмулятор) <br /><br />Разработка мобильных приложений с помощью .NET (пакеты SDK и NDK для Android, эмулятор) |
| www.incredibuild.com | Разработка игр с помощью C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Разработка игр с помощью C++ (IncrediBuild) |
| www.python.org | Разработка с помощью Python (Python) <br /><br />Приложения для обработки и анализа данных и аналитические приложения (Python) |
|  |  | |

## <a name="use-visual-studio-and-azure-services"></a>Использование Visual Studio и служб Azure

### <a name="urls-to-whitelist-and-ports-and-protocols-to-open"></a>URL-адреса для добавления в список разрешений, а также порты и протоколы для открытия

Ниже приведены URL-адреса доменов, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы обеспечить доступ к всем необходимым компонентам при использовании Visual Studio или служб Azure, расположенных за брандмауэром или прокси-сервером.

| Служба или сценарий | Конечная точка DNS | Протокол | Порт | Описание: |
| --- | --- | --- | --- | --- |
| URL-адрес<br>разрешение | go.microsoft.com<br><br>aka.ms | | |Используется для сокращения URL-адресов, которые затем разрешаются в длинные URL-адреса
| Начальная страница | vsstartpage.blob.core.windows.net | | 443| Используется для отображения новостей для разработчиков на начальной странице в Visual Studio |
| Целевая<br> Уведомление <br>Служба | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443| Используется для фильтрации глобального списка уведомлений, чтобы сделать его применимым только к определенным типам компьютеров и сценариев использования |
| Расширение <br>для расширения | visualstudiogallery.msdn.microsoft.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com  | | 443 | Используется для уведомления о доступном обновлении для установленного расширения <br><br> Используется как расположение для входа|
| Интеграция <br>Интеграция | az861674.vo.msecnd.net  | | 443<br> | Используется для настройки новых проектов и отправки данных об использовании в зарегистрированную учетную запись Application Insights |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | |443 | Используется для предоставления сведений в редакторе, например времени последнего обновления файла, временной шкалы изменений, связанных с изменениями рабочими элементами, данных о авторе и т. д.|
|Экспериментальный <br>экспериментальной функции  | visualstudio-devdiv-c2s.msedge.net | |80 | Используется для активации новых экспериментальных функций или измененных функций |
| Параметры индикатора событий для идентификации <br>(имя пользователя и аватар)<br>и <br>перемещения | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net  | |443 | Используется для отображения имени пользователя и аватара в среде IDE <br><br> Используется для перемещения изменений параметров с одного компьютера на другой |
| Настройки удаленной системы | az700632.vo.msecnd.net | | 443| Используется для отключения расширений, которые могут вызывать проблемы в работе Visual Studio   |
| Средства Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com |https |443 | Применяется для сценариев использования магазина приложений Windows  |
| Поддержка <br>Обнаружение <br><br>Поддержка <br>Определение<br><br>Поддержка <br>схемы JSON для <br>ресурсов Azure| json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com| http<br>https<br><br>http<br><br>https |80<br>443 <br><br> 443<br><br>443 | Используется для обнаружения и скачивания схем JSON, которые можно применять при изменении документов JSON <br><br>Используется для получения схемы проверки метаданных для JSON<br><br>Используется, чтобы получить текущую схему для шаблонов развертывания Azure Resource Manager|
| Обнаружение <br>обнаружение  |Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io  | https<br><br>http/s<br><br>https | 443<br><br>80/443<br><br>443| Требуется для поиска пакетов NPM и используется для установки клиентского пакета скриптов в веб-проектах |
|Значки<br> значки<br><br>Значки <br>search  |Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https|80<br><br>443<br>80<br>443 |Предоставляет значок по умолчанию для пакета Bower  <br><br>Позволяет выполнять поиск пакетов Bower |
|NuGet<br><br>Пакет NuGet<br> обнаружение | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com  | https<br><br>http/s |443<br><br>80/443<br> |Используется для проверки подписанных пакетов NuGet.<br><br>Требуется для поиска пакетов NuGet и их версий |
|Сведения о репозитории GitHub  |api.github.com  |https | 443| Требуется для получения дополнительных сведений о пакетах Bower |
| Веб-анализаторы кода|Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org  | http|80 | |
| Создание проекта<br>шаблонов обозревателя<br>обнаружение <br><br>Создание проекта <br>в обозревателе<br> Cookiecutter | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org  | https | 443<br> | Используется для обнаружения шаблонов в Интернете из рекомендуемого нами веб-канала и репозиториев GitHub <br><br>Используется для создания проекта из шаблона Cookiecutter, для которого требуется один раз по требованию установить пакет Python для Cookiecutter из индекса пакета Python (PyPI)|
| Управление <br>обнаружение<br><br>Управление <br>управление<br><br>Python <br>Создание проекта <br>шаблоны| pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com| https| 443| Позволяет выполнять поиск пакетов PIP<br><br>Используется для автоматической установки пакета PIP, если он отсутствует <br><br> Используется для создания <br><br>Используется для разрешения следующих шаблонов проектов Python в URL-адреса шаблонов Cookiecutter в диалоговом окне создания проекта:<br> — проект классификатора;<br>— проект кластеризации; <br> — проект регрессии; <br> — PyGame с использованием PyKinect; <br> — проект Pyvot. |
| Служба <br>надстройка <br> манифеста <br>Проверка <br>Служба | verificationservice.osi.office.net | https | 443 | Используется для проверки манифестов веб-надстроек Office |
| Веб-надстройки для SharePoint и <br>Office Add-ins | sharepoint.com | https | 443 | Используется для публикации и тестирования надстроек SharePoint и Office в SharePoint Online |
| Узел службы <br>тестирования<br> Ведущее приложение |  | http | 12292 | Правило брандмауэра, которое создается автоматически для тестирования надстроек SharePoint с помощью рабочих процессов |
| Автоматически собранные <br>статистические данные о надежности <br>и другие <br>программы улучшения качества <br>программного обеспечения (CEIP)<br> для пакета Azure SDK и <br>инструментов SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com |https | 443| Используется для отправки статистических данных о надежности (данные об аварийном завершении или зависании) от пользователя в корпорацию Майкрософт. Фактические дампы аварийного завершения или зависаний будут отправляться, даже если включено создание отчетов об ошибках Windows. Не будут отправляться только статистические данные. <br>Используется, чтобы выявить анонимное использование расширения пакета SDK для Azure Tools и средств SQL в Visual Studio |
| Visual Studio <br> программного обеспечения <br>Visual Studio <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https| 443 | Используется для сбора данных об анонимном использовании и журналов ошибок <br><br>Используется для отслеживания проблем блокировки пользовательского интерфейса|
| Создание и<br>администрирование <br>ресурсов Azure | management.azure.com <br>management.core.windows.net   | https | 443 | Используется для создания Веб-сайтов Azure и других ресурсов для поддержки публикаций веб-приложений, Функций Azure или веб-заданий |
| Рекомендации по <br>проверкам и расширениям <br>обновленного инструментария для веб-публикации  | marketplace.visualstudio.com  <br> visualstudiogallery.msdn.microsoft.com  | https | 443 | Используется для проверки доступности обновленного инструментария для публикации. Если эта конечная точка отключена, потенциально рекомендуемое расширение для веб-публикации может не отображаться |
| Сведения об обновленной <br>конечной точке для создания ресурсов Azure  | *.blob.core.windows.net | https | 443 | Применяется для обновления конечных точек, используемых при создании ресурсов Azure для определенных служб Azure. Если эта конечная точка отключена, будут использоваться расположения последней скачанной или встроенной конечной точки |
| Удаленная отладка и <br>удаленное профилирование <br>Веб-сайтов Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Используется для присоединения удаленного отладчика к Веб-сайтам Azure. Если эта конечная точка отключена, подключение удаленного отладчика к Веб-сайтам Azure будет невозможным |
| Active Directory <br>Graph | graph.windows.net | https | 443 | Используется для подготовки новых приложений Azure Active Directory. Также используется поставщиком подключенной службы MSGraph Office 365 |
| Проверка <br>обновлений CLI <br>службы "Функции Azure" | functionscdn.azureedge.net | https | 443 | Используется для проверки наличия обновленных версий CLI службы "Функции Azure". Если эта конечная точка отключена, будет использоваться кэшированная копия CLI (или копия, передаваемая компонентом "Функции Azure") |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | HTTP используется для скачивания Gradle во время сборки. HTTPS используется для включения подключаемых модулей Cordova в проекты|
| Cloud Explorer | 1. & #60;Конечная точка кластера& #62; <br>Service Fabric. <br>2. &#60;Конечная точка управления&#62;<br>Cloud Explorer общего назначения. <br>3. &#60;Конечная точка Graph&#62;<br>Cloud Explorer общего назначения.<br>4. &#60;Конечная точка учетной записи хранения&#62;:<br>узлы хранилища. <br>5. &#60;URL-адреса портала Azure&#62;:<br>Cloud Explorer общего назначения. <br>6. &#60;Конечные точки хранилища ключей&#62;: <br>узлы виртуальной машины Azure Resource Manager.<br>7. &#60;Общедоступный IP-адрес кластера&#62;:<br>удаленная отладка и трассировка ETW Service Fabric. |   <br>1. https.<br>2. https.<br>3. https.<br>4. https.<br>5. https.<br>6. https.<br>7. tcp| 1. 19080.<br>2. 443. <br>3. 443. <br>4. 443. <br>5. 443. <br>6. 443. <br>7. Динамический порт.   | 1. Пример: test12.eastus.cloudapp.com.<br>2. Позволяет извлекать данные о подписках и ресурсах, а также управлять ресурсами Azure.<br>3. Позволяет извлекать данные о подписках Azure Stack<br>4. Позволяет управлять ресурсами службы хранения (пример: mystorageaccount.blob.core.windows.net).<br>5. Пункт контекстного меню "Открыть на портале" (позволяет открыть элемент ресурса на портале Azure)<br>6. Позволяет создавать и использовать хранилища ключей для отладки виртуальной машины (пример: myvault.vault.azure.net) <br><br>7. Динамически выделяет блок портов с учетом числа узлов в кластере и доступных портов. <br><br>Блок портов выполняет три попытки получения узлов минимум с 10 портами.<br><br>При трассировке потоковой передачи выполняется попытка получить блок портов, начиная с 810. Если какой-либо из этих блоков портов уже используется, выполняется попытка получить следующий блок и т. д. (Если подсистема балансировки нагрузки пуста, скорее всего, будут использоваться порты, начиная с 810.) <br><br>Точно так же для отладки резервируется четыре блока портов: <br>— connectorPort: 30398; <br>— forwarderPort: 31398; <br>— forwarderPortx86: 31399;<br>— fileUploadPort: 32398.<br>|
| Облачные службы | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;пользовательская облачная служба&#62;.cloudapp.net <br> &#60;пользовательская виртуальная машина&#62;.&#60;region&#62;.azure.com | 1. rdp. <br><br> 2. https. <br><br> 3. https. <br><br> 4. https. <br><br> 5. https. <br><br>6. tcp. | 1. 3389. <br><br> 2. 443. <br><br> 3. 443. <br><br>4. 443. <br><br>5. 443. <br><br> 6. а) 30398 <br> 6. б) 30400 <br> 6. в) 31398 <br> 6. г) 31400 <br> 6. д) 32398 <br> 6. е) 32400 | 1.  Удаленный рабочий стол для виртуальной машины облачных служб <br><br> 2.  Компонент учетной записи хранения для диагностики закрытой конфигурации <br><br> 3.  порталу Azure <br><br> 4. Обозреватель сервера — служба хранилища Azure. &#42 ; — это имя пользовательской учетной записи хранения  <br><br> 5.  Ссылки для открытия портала. &#47 ; скачивания сертификата подписки &#47 ; публикации файла настроек <br><br>6. а) Локальный порт соединителя для удаленной отладки облачной службы и виртуальной машины<br> 6. б) Общий порт соединителя для удаленной отладки облачной службы и виртуальной машины <br> 6. в) Локальный порт сервера пересылки для удаленной отладки облачной службы и виртуальной машины <br> 6. г) Общий порт сервера пересылки для удаленной отладки облачной службы и виртуальной машины  <br> 6. д) Локальный порт средства загрузки файлов для удаленной отладки облачной службы и виртуальной машины <br> 6. е) Общий порт средства загрузки файлов для удаленной отладки облачной службы и виртуальной машины |
| Service Fabric. | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. Документация <br><br> 2. Функция создания кластера <br><br>3. Символ &#42; обозначает имя хранилища ключей Azure (пример: test11220180112110108.vault.azure.net)  <br><br>  4. Символ &#42; обозначает динамическую конечную точку (пример: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Снимок <br>Отладчик | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (в зависимости от версии Visual Studio) | 1. Запрос JSON-файла для размера SKU службы приложений <br>2. Различные вызовы Azure RM <br>3. Вызов первоначальной загрузки сайта  <br>4. Целевая конечная точка клиента службы консоли Kudu для службы приложений <br>5. Запрос версии расширения сайта, опубликованного на nuget.org <br>6. Канал удаленной отладки |
|Azure Stream Analytics <br><br>HDInsight | Management.azure.com |https|443 |Используется для просмотра, отправки, выполнения и администрирования заданий ASA <br><br> Используется для просмотра кластеров HDI, а также для отправки, диагностики и отладки заданий HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Используется для компиляции, отправки, просмотра, диагностики и отладки заданий. Также используется для просмотра файлов ADLS, а также отправки и скачивания файлов |
| Служба упаковки | [account].visualstudio.com <br/> [account].*.visualstudio.com <br/> *.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | Домены *.npmjs.org, *.nuget.org и *.nodejs.org требуются только для определенных сценариев, которые включают задачи сборки (например, установщик средств NuGet или Node) или в случае, если вы планируете использовать в своих веб-каналах общедоступные восходящие источники. Три других домена являются обязательными для работы с основными функциями службы упаковки. |
| VSTS | *.vsassets.io <br/> static2.sharepointonline.com  |  |  | Используется для подключения с помощью VSTS |
|||||||

## <a name="troubleshoot-network-related-errors"></a>Устранение ошибок сети

Иногда вы можете столкнуться с ошибками сети или прокси-сервера, которые возникают при установке или использовании решения Visual Studio, расположенного за брандмауэром или прокси-сервером. Дополнительные сведения об обработке сообщений об ошибках см. а руководстве по [исправлению ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Техническая поддержка

Ниже перечислены дополнительные варианты:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Исправление ошибок сети при установке или использовании Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)

