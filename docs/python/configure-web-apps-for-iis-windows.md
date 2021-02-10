---
title: Настройка веб-приложений Python для IIS
description: Сведения о настройке веб-приложений Python для запуска в службах IIS на виртуальной машине Windows.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 40411f47e7deda48b04ac4efb9bb9bc18688989a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839114"
---
# <a name="configure-python-web-apps-for-iis"></a>Настройка веб-приложений Python для IIS

При использовании служб IIS в качестве веб-сервера на компьютере под управлением Windows (включая [виртуальные машины Windows в Azure](/azure/architecture/reference-architectures/n-tier/windows-vm)) приложения Python должны содержать специальные параметры в файлах *web.config*, чтобы служба IIS могла правильно выполнить код Python. На самом компьютере также нужно установить интерпретатор Python вместе со всеми пакетами, необходимыми для веб-приложения.

> [!Note]
> Эта статья ранее содержала руководство по настройке приложений Python в службе приложений Azure на базе Windows. Теперь расширения Python и узлы Windows, использованные в таком сценарии, не рекомендуются к применению. Вместо них следует использовать службу приложений Azure на базе Linux. Дополнительные сведения см. в статье о [публикации приложений Python в службе приложений Azure (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Предыдущая статья по-прежнему доступна под заголовком [Работа с Python в Службе приложений Azure](managing-python-on-azure-app-service.md).

## <a name="install-python-on-windows"></a>Установка Python в Windows

Чтобы запустить веб-приложение, сначала установите нужную версию интерпретатора Python непосредственно на рабочий компьютер, как описано в [этой статье](installing-python-interpreters.md).

Запомните расположение интерпретатора `python.exe`. Он потребуется в дальнейшем. Для удобства это расположение можно добавить в переменную среды PATH.

## <a name="install-packages"></a>Установка пакетов

Если вы используете выделенный узел, можно запускать приложение в глобальном окружении Python, не создавая виртуальное окружение. Вы можете установить все зависимости приложения в глобальное окружение. Для этого достаточно ввести команду `pip install -r requirements.txt` в командной строке.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Указание интерпретатора Python в файле web.config

Файл *web.config* вашего приложения содержит сведения для веб-сервера IIS (версии 7 и более поздней версии), работающего в ОС Windows, о том, как обрабатывать запросы для приложения Python с помощью обработчика FastCGI или HttpPlatform (рекомендуется). Visual Studio 2015 и более ранних версий вносит эти изменения автоматически. При использовании Visual Studio 2017 и более поздних версий нужно изменить файл *web.config* вручную.

### <a name="configure-the-httpplatform-handler"></a>Настройка обработчика HttpPlatform

Модуль HttpPlatform передает подключения через сокет напрямую в автономный процесс Python. Такая сквозная передача позволяет запускать нужный веб-сервер, но требует выполнения скрипта запуска на локальном веб-сервере. Укажите скрипт в элементе `<httpPlatform>` файла *web.config*, где атрибут `processPath` указывает на интерпретатор Python для расширения сайта, а атрибут `arguments` указывает скрипт и содержит все аргументы для него:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Показанная здесь переменная среды `HTTP_PLATFORM_PORT` содержит порт, который должен прослушивать локальный сервер для соединений от localhost. Этот пример также показывает, как при необходимости создать другую переменную среды, в данном случае это `SERVER_PORT`.

### <a name="configure-the-fastcgi-handler"></a>Настройка обработчика FastCGI

FastCGI — это интерфейс, работающий на уровне запроса. Службы IIS принимают входящие подключения и перенаправляют каждый запрос в приложение WSGI, работающее в одном или нескольких сохраняемых процессах Python.

Для использования этого обработчика сначала установите и настройте пакет wfastcgi, как описано на странице [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi).

Далее измените файл *web.config* своего приложения, указав полные пути к файлам *python.exe* и *wfastcgi.py* в ключе `PythonHandler`. Для выполнения описанных ниже инструкций нужно, чтобы интерпретатор Python был установлен в папке *c:\python36-32*, а код приложения находился в папке *c:\home\site\wwwroot*. Укажите соответствующие пути:

1. Измените запись `PythonHandler` в файле *web.config* таким образом, чтобы путь соответствовал папке, где установлен Python. Точные сведения см. в [справочнике по настройке IIS](https://www.iis.net/configreference) (iis.net).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. В разделе `<appSettings>` файла *web.config* добавьте ключи `WSGI_HANDLER`, `WSGI_LOG` (не обязательно) и `PYTHONPATH`:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Эти значения `<appSettings>` доступны для вашего приложения в качестве переменных среды:

    - Значение `PYTHONPATH` можно свободно расширить, однако оно должно включать корень приложения.
    - `WSGI_HANDLER` должен указывать на приложение WSGI, импортируемое из приложения.
    - `WSGI_LOG` является необязательным, но рекомендуется для отладки приложения.

1. Задайте запись `WSGI_HANDLER` в файле *web.config* в соответствии с используемой платформой:

    - **Bottle.** Обязательно используйте скобки после `app.wsgi_app`, как показано ниже. Это необходимо, так как объект является функцией (см. *app.py*), а не переменной.

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: измените значение `WSGI_HANDLER` на `<project_name>.app`, где `<project_name>` соответствует имени проекта. Узнать точный идентификатор можно в операторе `from <project_name> import app` в файле *runserver.py*. Например, если проект имеет имя FlaskAzurePublishExample, эта запись будет выглядеть так:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: для проектов Django необходимо внести два изменения в файл *web.config*. Во-первых, измените значение `WSGI_HANDLER` на `django.core.wsgi.get_wsgi_application()` (объект находится в файле *wsgi.py*).

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Во-вторых, добавьте следующую запись под записью `WSGI_HANDLER`, заменив `DjangoAzurePublishExample` на имя проекта:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Только для приложений Django**: в файле *settings.py* проекта Django добавьте домен URL-адреса вашего сайта или его IP-адрес в параметр `ALLOWED_HOSTS`, как показано ниже, заменив "1.2.3.4" своим URL-адресом или IP-адресом:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Если не добавить URL-адрес в массив, возникнет ошибка **Запрещенный узел в / Недопустимый заголовок HTTP_HOST: "\<site URL\>". Возможно, необходимо добавить "\<site URL\>" в ALLOWED_HOSTS.**

    Обратите внимание, что, если массив пуст, Django автоматически разрешает localhost и "127.0.0.1". Но при добавлении URL-адреса рабочего развертывания эта возможность становится недоступной. Поэтому, возможно, потребуется создать отдельные копии *settings.py* для разработки и рабочей среды или использовать переменные среды, чтобы контролировать значения времени выполнения.

## <a name="deploy-to-iis-or-a-windows-vm"></a>Развертывание в службах IIS или на виртуальной машине Windows

При наличии правильно составленного файла *web.config* в вашем проекте вы можете опубликовать его на компьютере, где запущены службы IIS, воспользовавшись командой **Опубликовать** в контекстном меню проекта на вкладке **Обозреватель решений** и указав целевой объект — **IIS, FTP и т. п.** В этом случае Visual Studio просто скопирует файлы проекта на сервер. Настройку сервера вам необходимо выполнить самостоятельно.
