---
title: "Удаленная отладки ASP.NET в IIS на удаленном компьютере | Документы Microsoft"
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730a69894c8e38dd7b9d191fa7fe3396509148d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Удаленная отладка ASP.NET на IIS на удаленном компьютере
Для отладки приложений ASP.NET, IIS был развернут, установите и запустите инструменты удаленной отладки на компьютере, на котором развернуто приложение и прикрепите запущенного приложения из Visual Studio.

![Компоненты удаленной отладки](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

В этом руководстве объясняется, как установить и настроить приложение Visual Studio 2017 г. ASP.NET MVC 4.5.2, его развертывание в IIS и присоединить удаленный отладчик из Visual Studio. Удаленная отладка ASP.NET Core. в разделе [удаленной отладки ASP.NET Core на компьютере с IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Кроме того, можно развернуть и отладить в IIS с помощью Azure. Дополнительные сведения см. в разделе [удаленной отладки на платформе Azure](../debugger/remote-debugging-azure.md).

Эти процедуры протестированы на эти конфигурации сервера:
* Windows Server 2012 R2 и службы IIS 10 (для Windows Server 2008 R2, сервера используются разные процедуры)

## <a name="requirements"></a>Требования

Удаленный отладчик поддерживается в Windows Server, начиная с Windows Server 2008 с пакетом обновления 2. Полный список требований см. в разделе [требования](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Отладка между двумя компьютерами, подключенными через прокси-сервер не поддерживается. Отладка в различных странах через высокой задержкой или низкой пропускной способностью, таких как удаленный доступ к Интернету, либо через Интернет не рекомендуется и может произойти сбой или медленную неприемлемо.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Создание ASP.NET 4.5.2 приложение на компьютере Visual Studio
  
1. Создайте приложение MVC ASP.NET. (**Файл > Создать > проект**, а затем выберите ** Visual C# > Web > веб-приложения ASP.NET. В разделе шаблонов **ASP.NET 4.5.2** выберите шаблон **MVC**. Убедитесь, что **Включение поддержки Docker** не выбран и что **проверки подлинности** равно **без проверки подлинности**. Назовите проект **MyASPApp**.)

2. Откройте файл HomeController.cs и установите точку останова в методе `About()` .

## <a name="bkmk_configureIIS"></a>Установка и настройка служб IIS в Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Обновить параметры безопасности браузера в Windows Server

В зависимости от настроек безопасности он может сэкономить время, чтобы добавить следующие надежные сайты в браузер, поэтому можно легко загрузить программное обеспечение, описанный в этом учебнике. Возможно, потребуется доступ к этим сайтам:

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- загружаемые

При использовании Internet Explorer, можно добавить надежных сайтов, перейдя **свойства обозревателя > Безопасность > надежных узлов > сайтов**. Эти шаги для других браузеров различаются.

При загрузке программного обеспечения, можно получить запросы на предоставление разрешения на загрузку различные сценарии веб-сайт и ресурсы. В большинстве случаев эти дополнительные ресурсы не требуется устанавливать программное обеспечение.

## <a name="BKMK_deploy_asp_net"></a>Установка ASP.NET 4.5 на Windows Server

Если требуется более подробные сведения для установки ASP.NET на IIS, см. раздел [IIS 8.0 с помощью ASP.NET 3.5 и ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Используйте установщик веб-платформы (WebPI) для установки ASP.NET 4.5 (с узла сервера в Windows Server 2012 R2, выберите **получить новые компоненты платформы Web** и выполните поиск ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Если вы используете Windows Server 2008 R2, установите ASP.NET 4, вместо этого с помощью этой команды:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe - ir**

2. Перезагрузку системы (или выполните **net stop был /y** следуют **net start w3svc** из командной строки, чтобы отобразить изменение в системе путь).

## <a name="BKMK_install_webdeploy"></a>(Необязательно) Установка веб-развертывания 3.6 в Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>Настройка веб-сайта ASP.NET на сервере Windows Server

1. Откройте проводник Windows и создайте новую папку **C:\Publish**, где будут развернуты позднее проекта ASP.NET.

2. Откройте **Internet Information Services (IIS) Manager**. (В левой панели диспетчера серверов выберите **IIS**. Щелкните правой кнопкой мыши сервер и выберите **Диспетчер Internet Information Services (IIS)**.)

3. В разделе **подключений** в левой области выберите **узлы**.

4. Выберите **веб-сайт по умолчанию**, выберите **основные параметры**и задайте **физический путь** для **C:\Publish**.

5. Щелкните правой кнопкой мыши узел **Веб-сайт по умолчанию** и выберите команду **Добавить приложение**.

6. Задать **псевдоним** на **MyASPApp**, примите имя по умолчанию пула приложений (**DefaultAppPool**) и задайте **физический путь** для  **C:\Publish**.

7. В разделе **подключений**выберите **пулы приложений**. Откройте **DefaultAppPool** и задайте для поля пула приложений **ASP.NET v4.0** (ASP.NET 4.5 не предлагается для пула приложений).

8. С сайта, выбранного в диспетчере служб IIS, выберите **изменение разрешений**и убедитесь, что учетная запись IUSR, IIS_IUSRS или пользователь, настроен для пула приложений имеет полномочному пользователю с правами на чтение и выполнение. Если ни один из этих пользователей, добавление IUSR в качестве пользователя с правами на чтение и выполнение.

## <a name="bkmk_webdeploy"></a>(Необязательно) Публикация и развертывание приложения с помощью веб-развертывание из Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

Кроме того, необходимо ознакомиться с разделом [Устранение неполадок порты](#bkmk_openports).

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Необязательно) Публикация и развертывание приложения путем публикации в локальную папку из Visual Studio

Можно также опубликовать и развертывание приложения с помощью файловой системы или других средств.

1. (ASP.NET 4.5.2) Убедитесь, что в файле web.config указана правильная версия платформы .NET Framework.  Например при разработке проектов для ASP.NET 4.5.2, убедитесь, что эта версия указана в файле web.config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Например версия должна быть 4.0 при установке ASP.NET 4 вместо 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Загрузите и установите инструменты удаленной отладки на Windows Server

В этом учебнике мы используем Visual Studio 2017 г.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> В некоторых сценариях может быть наиболее эффективным для запуска удаленного отладчика из общей папки. Дополнительные сведения см. в разделе [запуск удаленного отладчика из общей папки](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a>Настройка удаленного отладчика на Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Если необходимо добавить разрешения для других пользователей, изменение режима проверки подлинности, или номер порта удаленного отладчика, в разделе [настроить удаленный отладчик](../debugger/remote-debugging.md#configure_msvsmon).

Сведения на запуск удаленного отладчика в качестве службы см. в разделе [запуска удаленного отладчика в качестве службы](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Подключение к приложению ASP.NET с компьютера с Visual Studio

1. На компьютере с Visual Studio, откройте **MyASPApp** решения.
2. В Visual Studio щелкните **Отладка > присоединить к процессу** (Ctrl + Alt + P).

    > [!TIP]
    > В Visual Studio 2017 г., можно подключить с тем же процессом, ранее присоединена к с помощью **Отладка > повторно присоединиться к процессу...** (Shift + Alt + P). 

3. Задайте для поля квалификатор  **\<имя удаленного компьютера >: 4022**.
4. Нажмите кнопку **Обновить**.
    В окне **Доступные процессы** должен появиться ряд процессов.

    Если вы не видите все процессы, попробуйте использовать IP-адрес вместо имени удаленного компьютера (порт является обязательным). Можно использовать `ipconfig` в командной строке, чтобы получить адрес IPv4.

5. Установите флажок  **Показать процессы, запущенные всеми пользователями**.
6. Введите имя процесса, чтобы быстро найти первую букву **w3wp.exe** для ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Нажмите кнопку **присоединения**

8. Откройте веб-сайт удаленного компьютера. В браузере, перейдите к **http://\<имя удаленного компьютера >**.
    
    Должна открыться веб-страница ASP.NET.
9. В работающем приложении ASP.NET, щелкните ссылку, чтобы **о** страницы.

    В Visual Studio должна быть достигнута точка останова.

## <a name="bkmk_openports"></a>Устранение неполадок: Откройте требуемых портов в Windows Server

В большинстве установок необходимые порты открыты путем установки ASP.NET и удаленный отладчик. Тем не менее может потребоваться проверить, что открыты порты.

> [!NOTE]
> На виртуальной Машине Azure, необходимо открыть порты, через [сетевой группы безопасности](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Необходимые порты:

- 80 - требуется для служб IIS
- 8172 - (требуется необязательно) для веб-развертывания для развертывания приложения из Visual Studio
- 4022 - необходимых для удаленной отладки из Visual Studio 2017 г. (см. [назначение портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md) подробные сведения.
- UDP 3702 - порта (необязательно) обнаружения позволяет **найти** кнопку при присоединении удаленного отладчика в Visual Studio.

1. Чтобы открыть порт на сервере Windows, откройте **запустить** меню, поиск **брандмауэр Windows в режиме повышенной безопасности**.

2. Выберите **правила для входящих подключений > новое правило > порт**. Выберите **Далее** и в разделе **определенные локальные порты**, введите номер порта, нажмите кнопку **Далее**, затем **Разрешить соединение**, нажмите кнопку Далее, и Добавьте имя (**IIS**, **веб-развертывания**, или **msvsmon**) для правила входящего подключения.

    Если для получения дополнительных сведений о настройке брандмауэра Windows см. раздел [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Создайте дополнительные правила для требуемых портов.