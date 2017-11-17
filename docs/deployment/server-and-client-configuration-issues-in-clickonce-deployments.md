---
title: "Вопросы настройки клиента в развертываниях ClickOnce сервера и | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Вопросы настройки сервера и клиента в развертываниях ClickOnce
При использовании Internet Information Services (IIS) в Windows Server, и развертывание содержит тип файла, который не распознается Windows, например файл Microsoft Word, службы IIS откажут в передаче этого файла и не будет выполнено развертывание.  
  
 Кроме того, некоторые веб-серверов и веб-приложений, таких как [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], содержит список файлов и типов файлов, которые не удается загрузить. Например [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] предотвращает загрузку всех файлов Web.config. Эти файлы могут содержать конфиденциальные сведения, например имена пользователей и пароли.  
  
 Несмотря на то, что это ограничение должно не приводить к проблемам загрузки основных [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлы, такие как манифесты и сборки, это ограничение может препятствовать загрузке файлов данных, включаемых в рамках вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. В [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], эту ошибку можно устранить путем удаления обработчика, который запрещает загрузку таких файлов, из диспетчера конфигурации служб IIS. См. в документации сервера IIS для получения дополнительных сведений.  
  
 Некоторые веб-серверы могут блокировать файлы с расширениями DLL-файл, config и mdf. Windows-приложениях обычно относятся файлы с некоторыми из этих расширений. Если пользователь попытается запустить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, которое обращается к заблокированный файл на веб-сервере, будет выдана ошибка. Вместо разблокирования всех расширений файлов, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] публикует каждый файл приложения с расширением файла «.deploy» по умолчанию. Таким образом, администратору необходимо только настроить веб-сервер, чтобы разблокировать трех расширений файлов:  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 Тем не менее, этот параметр можно отключить, сняв **использовать расширение файла «.deploy»** параметр [параметры публикации](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), в этом случае необходимо настроить веб-сервер, чтобы разблокировать все расширения файлов используемые в приложении.  
  
 Необходимо будет настроить .manifest .application и .deploy, например, при использовании служб IIS, где не установлена [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], или если вы используете другой веб-сервер (например, Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce и Secure Sockets Layer (SSL)  
 Объект [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение будет работать по протоколу SSL, за исключением случаев, когда Internet Explorer инициирует запрос SSL-сертификат. Запрос может возникнуть, когда существует проблема с сертификат, например когда имена узлов не совпадают или сертификата истек. Чтобы сделать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] работать через SSL-подключение, убедитесь, что сертификат обновлен и соответствие данным сайта в данных сертификата.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce и проверка подлинности прокси-сервера  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]предоставляет поддержку для интеграции с Windows проверка подлинности прокси-сервера, начиная с .NET Framework 3.5. Нет определенных Machine.config не требуется. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]предоставляет поддержку для других протоколов проверки подлинности, такие как обычную или дайджест.  
  
 Можно также установить исправление для .NET Framework 2.0, чтобы включить эту функцию. Дополнительные сведения см. в разделе http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Дополнительные сведения см. в разделе [ \<defaultProxy > Element (Network Settings)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce и веб-браузер совместимость  
 В настоящее время [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установок запускаются только в том случае, если URL-адрес манифеста развертывания открывается с помощью Internet Explorer. Развертывание, URL-адрес которого открывается из другого приложения, например Microsoft Office Outlook, успешно запускаются только в том случае, если Internet Explorer настроен как веб-браузер по умолчанию.  
  
> [!NOTE]
>  Mozilla Firefox поддерживается в том случае, если поставщик развертывания не является пустым или установлено расширение помощника Microsoft .NET Framework. Это расширение упаковывается вместе с .NET Framework 3.5 SP1. Для поддержки XBAP при необходимости активируется подключаемый модуль NPWPF.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Активация приложений ClickOnce с помощью скриптов браузера  
 Если вы разработали пользовательские веб-страницы, которая запускает [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, использующего элементы управления ActiveX, может оказаться, что приложение не будет запускаться на некоторых компьютерах. Internet Explorer содержит параметр **автоматический запрос загрузки файла**, что влияет на это поведение. Этот параметр доступен на **безопасности** вкладку в его **параметры** меню влияет на это поведение. Он вызывается **автоматический запрос загрузки файла**, и указываются под **загружает** категории. Свойство имеет значение **включить** по умолчанию для веб-страниц интрасети, а также **отключить** по умолчанию для веб-страниц. Если значение этого параметра **отключить**, любая попытка активировать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения программным способом (например, назначив его URL-адрес для `document.location` свойство) будут заблокированы. В этих условиях пользователи могут например, запускать приложения только через инициируемую пользователем загрузку, щелкнув гиперссылку, задать URL-адрес приложения.  
  
## <a name="additional-server-configuration-issues"></a>Дополнительные вопросы настройки сервера  
  
##### <a name="administrator-permissions-required"></a>Требуются права администратора  
 При публикации с использованием HTTP, необходимо иметь разрешения администратора на целевом сервере. Данный уровень разрешений требуется IIS. Если не публикуются с использованием HTTP, только необходимо разрешение на запись по конечному пути.  
  
##### <a name="server-authentication-issues"></a>Вопросы проверки подлинности сервера  
 При публикации на удаленный сервер, имеющий отключена «анонимный доступ», появится следующее предупреждение:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Можно сделать проверку подлинности NTLM (NT запрос ответ) недоступны, если узел запрашивает учетные данные, отличные от учетные данные по умолчанию, и в диалоговом окне "Безопасность" выберите **ОК** при запросе, если вы хотите сохранить предоставленного учетные данные для будущих сеансов. Однако этот способ не будет работать для обычной проверки подлинности.  
  
## <a name="using-third-party-web-servers"></a>Использование сторонних веб-серверов  
 Если вы развертываете [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с веб-сервера, отличные от IIS, проблема может возникнуть, если сервер возвращает неверный тип содержимого для ключа [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлов, таких как манифест развертывания и манифест приложения. Чтобы устранить эту проблему, содержатся в справке веб-сервере документации о том, как добавить новые типы содержимого на сервер и убедитесь, что все сопоставления расширений имен файлов, перечисленные в следующей таблице будут на месте.  
  
|Расширение имени файла|Тип содержимого|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce и подключенные сетевые диски  
 При использовании Visual Studio для публикации приложения ClickOnce, нельзя указать подключенный диск как расположение установки. Тем не менее можно изменить приложение ClickOnce для установки с подключенного диска с помощью создания и редактирования манифеста (Mage.exe и MageUI.exe). Дополнительные сведения см. в разделе [Mage.exe (средство создания и манифеста редактирования)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) и [MageUI.exe (средство создания и манифеста редактирования, графический клиент)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Протокол FTP не поддерживается для установки приложений  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]поддерживает установку приложений с любого файлового сервера или 1.1 веб-сервера HTTP. FTP, протокол передачи файлов не поддерживается для установки приложений. Только для публикации приложений можно использовать протокол FTP. В следующей таблице приведены эти различия:  
  
|Тип URL-адреса|Описание|  
|--------------|-----------------|  
|FTP: / /|Вы можете опубликовать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью этого протокола.|  
|http://|Можно установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью этого протокола.|  
|https://|Можно установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью этого протокола.|  
|file://|Можно установить [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения с помощью этого протокола.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Брандмауэр Windows  
 По умолчанию в Windows XP с пакетом обновления 2 включает брандмауэр Windows. Если вы разрабатываете приложение на компьютере с установленной операционной системой Windows XP, по-прежнему можно публиковать и выполнять [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений с локального сервера, на котором работает IIS. Тем не менее не может получить доступ к этом сервере, где работают службы IIS с другого компьютера, если открыть брандмауэр Windows. Инструкции по управлению брандмауэра Windows см.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Включение серверных расширений FrontPage  
 Серверные расширения FrontPage от Майкрософт является обязательным для публикации приложений на веб-сервера Windows, используется протокол HTTP.  
  
 По умолчанию Windows Server не имеет установлены серверные расширения FrontPage. Если вы хотите использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для публикации на сервере Windows Server Web, который использует протокол HTTP с помощью серверных расширений FrontPage, необходимо установить серверные расширения FrontPage сначала. Установку можно выполнить с помощью средства администрирования управление сервером в Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Типы содержимого заблокированной  
 Службы IIS на [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] блокируют все типы файлов, за исключением определенных известных типов содержимого (например, файлы HTM, HTML, .txt и т. д). Чтобы включить развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений, использующих этот сервер, необходимо изменить параметры служб IIS для разрешения загрузки файлов типа ".Application", с расширением MANIFEST и любых других настраиваемых типов файлов, используемого приложением.  
  
 При развертывании с помощью IIS-сервер, запустите inetmgr.exe и добавьте новые типы файлов для веб-страницы по умолчанию:  
  
-   Для расширений .application и .manifest тип MIME должен быть «приложение/x-ms приложение». Для других типов файлов тип MIME должен быть «application/octet-stream».  
  
-   При создании типа MIME с расширением «*», тип MIME «application/octet-stream», позволяющая тип разблокировать файл для загрузки файлов. (Однако блокируется файл, который не удается загрузить типы, например .aspx, .asmx).  
  
 Сведения о настройке типов MIME в Windows Server, обратитесь к статье базы знаний Майкрософт KB326965, «IIS 6.0 Does не обслуживать неизвестные типы MIME» в [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Сопоставления типов содержимого  
 При публикации по протоколу HTTP, тип содержимого (также известные как тип MIME) для файла .application должно быть «приложения/x-ms приложение». Если у вас есть [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] установлен на сервере, это будет задано для вас автоматически. Если это не установлен, то необходимо создать ассоциацию MIME-тип для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] виртуального корня приложения (или всего сервера).  
  
 При развертывании с помощью IIS-сервер, запустите inetmgr.exe и добавьте новый тип содержимого «приложение/x-ms-приложения» для расширением .application.  
  
## <a name="http-compression-issues"></a>Проблемы сжатие HTTP  
 С [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], можно выполнять загрузки, использующие HTTP-сжатие, технологию веб-сервера, который использует алгоритм GZIP для сжатия потока данных перед отправкой потока клиенту. Клиент — в этом случае [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— разворачивает поток, перед тем как читать файлы.  
  
 Если используются службы IIS, можно легко включить HTTP-сжатия. Однако при включении HTTP-сжатия оно включается только для определенных типов файлов, а именно, HTML и текстовых файлов. Чтобы включить сжатие для сборок (.dll), XML (.xml), манифестов развертывания (.application) и манифестов приложений (.manifest), необходимо добавить эти типы файлов в список типов для сжатия службами IIS. Пока вы не добавите типы файлов для развертывания, будет сжат только текст и HTML-файлы.  
  
 Подробные инструкции для служб IIS см. в разделе [способы указания дополнительных типов документов для HTTP-сжатия](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)