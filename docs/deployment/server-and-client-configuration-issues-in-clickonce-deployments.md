---
title: Проблемы конфигурации сервера и клиента в развертываниях ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71b9df9a8422d1b24a3e5476005942113356c353
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747427"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Вопросы настройки сервера и клиента в развертываниях ClickOnce
Если вы используете Internet Information Services (IIS) в Windows Server, и развертывание содержит тип файла, который не распознается Windows, например файл Microsoft Word, сервер IIS не будет передавать этот файл и не будет выполнено развертывание.

 Кроме того, некоторые веб-серверы и веб-приложения, такие как [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], содержат список файлов и типов файлов, которые не удается загрузить. Например [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] предотвращает загрузку всех *Web.config* файлов. Эти файлы могут содержать конфиденциальные сведения, такие как имена пользователей и пароли.

 Несмотря на то, что это ограничение должно вызывать никаких проблем загрузки основных [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлы манифестов и сборок, это ограничение может препятствовать загрузке файлов данных, являющемся частью вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. В [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], эту ошибку можно устранить путем удаления обработчика, который запрещает загрузку таких файлов, из диспетчера конфигурации служб IIS. См. в документации по IIS server для получения дополнительных сведений.

 Некоторые веб-серверы могут блокировать файлы с расширениями, такие как *.dll*, *.config*, и *.mdf*. Приложения на основе Windows, как правило, содержат файлы с некоторыми из этих расширений. Если пользователь попытается запустить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение, обращающееся к заблокированного файла на веб-сервере, будет выдана ошибка. Вместо того, чтобы разблокировать все расширения файлов, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] публикует каждый файл приложения с *.deploy* расширение файла по умолчанию. Таким образом администратор должен только для настройки веб-сервер, чтобы разблокировать следующие три файла расширения:

- *.application*

- *.manifest*

- *.deploy*

  Тем не менее, этот параметр можно отключить, сняв **использовать расширение файла «.deploy»** параметр [Publish Options Dialog Box](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)), в этом случае необходимо настроить веб-сервер, чтобы разблокировать все расширения файлов используемые в приложении.

  Вы должны будете настроить *.manifest*, *.application*, и *.deploy*, например, если используются службы IIS, где не установлена платформа .NET Framework, или если вы являетесь с помощью другого веб-сервера (например, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce и Secure Sockets Layer (SSL)
 Объект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение будет работать по протоколу SSL, за исключением случаев, когда Internet Explorer инициирует запрос SSL-сертификат. Запрос может инициироваться, когда существует проблема с сертификат, например когда имена узлов не совпадают или сертификата истек. Чтобы сделать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] работать через SSL-подключение, убедитесь, что сертификат находится в актуальном состоянии, а данные сертификата соответствует данные сайта.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce и прокси-сервер проверки подлинности
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] предоставляет поддержку для интеграции Windows проверка подлинности прокси, начиная с версии .NET Framework 3.5. Нет определенных Machine.config не требуется. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] предоставляет поддержку для других протоколов проверки подлинности как Basic или Digest.

 Можно также применить исправление для .NET Framework 2.0, чтобы включить эту функцию. Дополнительные сведения см. в разделе http://go.microsoft.com/fwlink/?LinkId=158730.

 Дополнительные сведения см. в разделе [ \<defaultProxy > (сетевые параметры)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce и веб-браузерами
 В настоящее время [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установок запускаются только в том случае, если URL-адрес манифеста развертывания открывается с помощью Internet Explorer. Развертывание, URL-адрес которого открывается из другого приложения, такие как Microsoft Office Outlook, успешно запускаются только в том случае, если Internet Explorer устанавливается как веб-браузер по умолчанию.

> [!NOTE]
> Mozilla Firefox поддерживается в том случае, если поставщик развертывания не является пустым или установке расширения Microsoft .NET Framework Assistant. Это расширение поставляется в комплекте с .NET Framework 3.5 SP1. Для поддержки XBAP подключаемый модуль NPWPF активируется при необходимости.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Активация приложений ClickOnce с помощью обозревателя сценариев
 Если вы разработали пользовательской веб-страницы, которая запускает [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью активных сценариев, вы обнаружите, что приложение не будет запускаться на некоторых компьютерах. Internet Explorer содержит параметр **автоматический запрос загрузки файла**, что негативно влияет на это поведение. Этот параметр можно найти в **безопасности** вкладке его **параметры** меню, которое влияет на это поведение. Он называется **автоматический запрос загрузки файла**, и содержится **загружает** категории. Свойство имеет значение **включить** по умолчанию для веб-страниц интрасети, а также **отключить** по умолчанию для веб-страниц Интернета. Если присвоить этот параметр **отключить**, любая попытка активировать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения программным способом (например, назначив его URL-адреса `document.location` свойство) будут заблокированы. В этих условиях пользователи могут, запускать приложения только через загрузки, инициированного пользователем, щелкнув гиперссылку, задать URL-адрес приложения.

## <a name="additional-server-configuration-issues"></a>Дополнительные вопросы настройки сервера

##### <a name="administrator-permissions-required"></a>Требуются разрешения администратора
 При публикации с помощью HTTP, необходимо иметь разрешения администратора на целевом сервере. Данный уровень разрешений требуется IIS. Если вы не публикуете с помощью протокола HTTP, только разрешение на запись необходимо по конечному пути.

##### <a name="server-authentication-issues"></a>Вопросы проверки подлинности сервера
 При публикации на удаленный сервер, имеющий отключена «анонимный доступ», вы получите следующее предупреждение:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Можно сделать проверку подлинности NTLM (NT запрос ответ) работать, если узел запрашивает учетные данные, отличные от учетные данные по умолчанию, а в диалоговом окне "Безопасность" нажмите кнопку **ОК** при появлении запроса, если вы хотите сохранить предоставленного учетные данные для будущих сеансов. Тем не менее это решение не будет работать для обычной проверки подлинности.

## <a name="use-third-party-web-servers"></a>Использовать сторонние веб-серверов
 Если вы развертываете [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение из веб-сервера, отличные от IIS, проблема может возникнуть, если сервер возвращает неверный тип содержимого для ключа [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлы, такие как манифест развертывания и манифест приложения. Чтобы устранить эту проблему, см. в разделе документации о том, как добавить новые типы содержимого на сервере и убедитесь, что все сопоставления расширений имен файлов, перечисленных в следующей таблице у вас есть справки веб-сервере.

|Расширение имени файла|Тип содержимого|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce и подключенные диски
 Если вы используете Visual Studio для публикации приложения ClickOnce, нельзя указать подключенный диск размещения установки. Тем не менее можно изменить приложение ClickOnce для установки с подключенного диска, с помощью создания и редактирования манифеста (Mage.exe и MageUI.exe). Дополнительные сведения см. в разделе [Mage.exe (средство редактирования и Manifest Generation)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) и [MageUI.exe (средство создания и редактирования манифестов, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Протокол FTP, не поддерживается для установки приложений
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] поддерживает установку приложений с любого файлового сервера или 1.1 веб-сервера HTTP. FTP, протокол передачи файлов не поддерживается для установки приложений. FTP можно использовать только для публикации приложений. В следующей таблице перечислены эти различия:

| Тип URL-адреса | Описание |
|----------| - |
| ftp:// | Вы можете опубликовать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с помощью этого протокола. |
| http:// | Вы можете установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с помощью этого протокола. |
| https:// | Вы можете установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с помощью этого протокола. |
| file:// | Вы можете установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с помощью этого протокола. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP с пакетом обновления 2 (SP2): Брандмауэр Windows
 По умолчанию в Windows XP с пакетом обновления 2 включает брандмауэр Windows. Если вы разрабатываете приложение на компьютере с установленной операционной системой Windows XP, вы по-прежнему публикации и запуску [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с локального сервера, где работают службы IIS. Тем не менее не может получить доступ к этом сервере, где работают службы IIS с другого компьютера, если не открыть брандмауэр Windows. Инструкции по управлению брандмауэром Windows содержатся в справке Windows.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Включить серверные расширения FrontPage
 Серверные расширения FrontPage от Майкрософт является обязательным для публикации приложений на сервере Windows, используется протокол HTTP.

 По умолчанию в Windows Server нет установлены серверные расширения FrontPage. Если вы хотите использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для публикации на сервере Windows Server Web, который использует протокол HTTP с помощью серверных расширений FrontPage, вам сначала необходимо установить серверные расширения FrontPage. Установку можно выполнить с помощью средства администрирования Управление данным сервером в Windows Server.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: Заблокированная типы содержимого
 Службы IIS на [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] блокируют все типы файлов, за исключением определенных известных типов содержимого (например, *.htm*, *.html*, *.txt*, и так далее). Чтобы включить развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений, использующих этот сервер, необходимо изменить параметры IIS для разрешения загрузки файлов типа *.application*, *.manifest*и любых других настраиваемых типов файлов используемый приложением.

 Если развертывание выполняется с помощью сервера IIS, запустите *inetmgr.exe* и добавить новые типы файлов для веб-страницы по умолчанию:

- Для *.application* и *.manifest* расширения, тип MIME должен быть «application/x-ms приложение». Для других типов файлов тип MIME должен быть «application/octet-stream».

- Если создать тип MIME с расширением "<em>", тип MIME «application/octet-stream», позволяющая тип разблокировать файл для загрузки файлов. (Тем не менее, блокируемыми типами файлов, таких как *.aspx</em> и *.asmx* не могут быть загружены.)

  Конкретные инструкции по настройке типы MIME в Windows Server, см. в статье базы знаний Майкрософт KB326965, «IIS 6.0 не обслуживает неизвестные типы MIME» в [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).

## <a name="content-type-mappings"></a>Сопоставления типов содержимого
 При публикации по протоколу HTTP, тип содержимого (также известный как тип MIME) для *.application* файл должен быть «application/x-ms приложение». Если у вас есть .NET Framework 2.0 установлен на сервере, это будут устанавливаться для вас автоматически. Если это не установлен, то необходимо создать ассоциацию MIME-типа для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] виртуального корня приложения (или всего сервера).

 Если развертывание выполняется с помощью сервера IIS, запустите <em>inetmgr.</em> EXE-файл и добавить новый тип содержимого «application/x-ms приложение» для *.application* расширения.

## <a name="http-compression-issues"></a>Проблемы сжатие HTTP
 С помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], можно выполнять загрузки с помощью HTTP-сжатие, технологию веб-сервера, который использует алгоритм GZIP для сжатия потока данных перед отправкой потока клиенту. Клиент — в этом случае [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— разворачивает поток перед чтением файлов.

 Если используются службы IIS, вы можете легко включить сжатие HTTP. Тем не менее, при активации сжатия HTTP, она включена только для определенных типов файлов, а именно, HTML и текстовые файлы. Чтобы включить сжатие для сборок ( *.dll*), XML ( *.xml*), манифесты развертывания ( *.application*) и манифесты приложений ( *.manifest*), необходимо добавить этих файлов типы в списке типов для сжатия службами IIS. Пока вы не добавите типы файлов для развертывания, будет сжат только текст и HTML-файлы.

 Подробные инструкции для служб IIS см. в разделе [способы указания дополнительных типов документов для сжатия HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).

## <a name="see-also"></a>См. также
- [Устранение неполадок развертываний ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)