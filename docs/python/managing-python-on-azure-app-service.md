---
title: "Работа с Python в службе приложений Azure | Документы Майкрософт"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 5b509a46dd3dbee3a45ab2eac57242636beee17b
ms.contentlocale: ru-ru
ms.lasthandoff: 07/18/2017

---

# <a name="managing-python-on-azure-app-service"></a>Работа с Python в службе приложений Azure

[Служба приложений Azure](https://azure.microsoft.com/services/app-service/) — это предложение вида "платформа как услуга" для веб-приложений, представлены ли они сайтами, к которым обращаются через браузер, REST API, используемыми вашими собственными клиентами, либо обработкой с активацией по событиям. Служба приложений полностью поддерживает использование Python для реализации приложений.

Поддержка Python в службе приложений Azure представлена набором расширений сайтов, каждое из которых содержит определенную версию среды выполнения Python. Рекомендуется последняя версия Python 3, но в случае необходимости можно использовать и более старую. Этот раздел описывает установку и настройку расширения сайта, а также всех нужных пакетов.

> [!Note]
> Представленные здесь процедуры могут изменяться, в частности, для их улучшения. Сведения об изменениях публикуются в [блоге Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Выбор версии Python с помощью портала Azure

Если ваш сайт уже развернут и запущен в службе приложений Azure, перейдите в раздел **Инструменты разработчика** колонки "Служба приложений" и выберите **Расширения > Добавить**. Прокрутите список и найдите конкретные расширения для нужной версии Python (к сожалению, этот список не поддерживает сортировку, поэтому различные версии часто разнесены по списку):

![Портал Azure с расширениями Python](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Выбор версии Python с помощью Azure Resource Manager

Если вы развертываете сайт с помощью шаблона Azure Resource Manager, добавьте расширение сайта в качестве ресурса. Это расширение отображается в виде вложенного ресурса сайта с типом `siteextensions` и именем из [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Например, после добавления ссылки на `python361x64` (Python 3.6.1 x64) шаблон может выглядеть следующим образом:

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>Настройка сайта

После установки расширения сайта (с помощью портала или шаблона Azure Resource Manager) путь установки Python будет похож на `d:\home\python361x64\python.exe`. Для просмотра конкретного пути выберите расширение в списке, отображаемом для службы приложений, чтобы открыть страницу с описанием, где указан путь:

![Список расширений в службе приложений Azure](media/python-on-azure-extension-list.png)

![Сведения о расширении в службе приложений Azure](media/python-on-azure-extension-detail.png)

Следующий шаг заключается в указании ссылки на установку Python в файле `web.config` сайта для обработчиков запросов платформы HTTP и FastCGI.

### <a name="using-the-fastcgi-handler"></a>Использование обработчика FastCGI

FastCGI — это интерфейс, работающий на уровне запроса. Службы IIS принимают входящие подключения и перенаправляют каждый запрос в приложение WSGI, работающее в одном или нескольких сохраняемых процессах Python. [Пакет wfastcgi](https://pypi.io/project/wfastcgi) предварительно установлен и настроен для каждого расширения сайта Python, поэтому вы можете легко включить его, добавив следующий код в `web.config`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` доступны для вашего приложения в качестве переменных среды:
- Значение для `PYTHONPATH` можно свободно расширить, однако оно должно включать корень сайта.
- `WSGI_HANDLER` должен указывать на приложение WSGI, импортируемое с сайта.
- `WSGI_LOG` является необязательным, но рекомендуется для отладки сайта. 

В разделе `<handlers>` включите в атрибут `scriptProcessor` элемента `<add>` правильные пути к конкретной установке. Путь снова отображается в колонке сведений о расширении.

### <a name="using-the-http-platform-handler"></a>Использование обработчика платформы HTTP

Модуль HttpPlatform передает подключения через сокет напрямую в автономный процесс Python. Такая сквозная передача позволяет запускать нужный веб-сервер, но требует выполнения скрипта запуска на локальном веб-сервере. Укажите скрипт в элементе `<httpPlatform>`, где атрибут `processPath` указывает на Python, а атрибут `arguments` — на скрипт и все нужные аргументы:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Конечно же, путь к `python.exe` в вашей конфигурации зависит от установленной версии.

Показанная в коде переменная среды `HTTP_PLATFORM_PORT` содержит порт, который должен прослушивать локальный сервер для соединений от localhost. Этот пример также показывает, как при необходимости создать другую переменную среды, в данном случае это `SERVER_PORT`.

## <a name="installing-packages"></a>Установка пакетов

Так как приложение, скорее всего, зависит от множества пакетов, вам нужно установить эти пакеты для своего окружения Python в службе приложений с помощью одного из трех способов:

- Консоль службы приложений Azure на портале Azure
- REST API Kudu
- Копирование каждой библиотеки в исходный код приложения

### <a name="kudu-console"></a>Консоль Kudu

[Консоль Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) предоставляет вам прямой доступ к серверу службы приложений и его файловой системе из командной строки с повышенными привилегиями. Этот инструмент удобно использовать при отладке, а также можно применять для конфигураций на основе интерфейса командной строки.

Откройте Kudu из колонки службы приложений, выбрав **Инструменты разработчика > Дополнительные инструменты**, а затем выберите **Перейти** для перехода по URL-адресу, который совпадает с вашим базовым URL-адресом службы приложений, за исключением вставленного элемента `.scm`. Например, если базовый URL-адрес имеет вид `https://vspython-test.azurewebsites.net/`, то для Kudu используется `https://vspython-test.scm.azurewebsites.net/`:

![Консоль Kudu для службы приложений Azure](media/python-on-azure-console01.png)

Выберите **Консоль отладки > CMD**, чтобы открыть консоль, где можно перейти к установке Python и узнать, какие библиотеки уже доступны.

Установка отдельного пакета:

1. Перейдите в папку установки Python, куда хотите установить пакет, например `d:\home\python361x64`.
1. Используйте команду `python.exe -m pip install <package_name>` для установки пакета.

![Пример установки matplotlib через консоль Kudu для службы приложений Azure](media/python-on-azure-console02.png)

Установка пакетов из файла `requirements.txt` (рекомендуется):

1. Перейдите в папку установки Python, куда хотите установить пакет, например `d:\home\python361x64`.
1. Используйте команду `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` для установки пакета.

Файл requirements.txt рекомендуется использовать, так как он позволяет легко воспроизвести точный набор пакетов как в локальной среде, так и на сервере.

> [!Note]
> На веб-сервере нет компилятора C, поэтому нужно установить "колесо" (wheel) для всех пакетов с собственными модулями расширения. Многие популярные пакеты имеют свои собственные колеса. В противном случае используйте `pip wheel <package_name>` на локальном компьютере разработки, после чего отправьте колесо на сайт. Пример см. в разделе [Управление необходимыми пакетами](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>REST API Kudu

Вместо использования консоли Kudu на портале Azure можно выполнять команды удаленно через REST API Kudu, публикуя их по адресу `https://yoursite.scm.azurewebsites.net/api/command`. Например, чтобы установить пакет `matplotlib`, опубликуйте следующую JSON по адресу `/api/command`:

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Сведения о командах и проверке подлинности см. в [документации по Kudu](https://github.com/projectkudu/kudu/wiki/REST-API). Вы также можете просмотреть учетные данные с помощью [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) из Azure CLI. Вспомогательную библиотеку для публикации команд Kudu также можно найти на сайте GitHub] (https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Копирование библиотек в исходный код приложения

Вместо установки пакетов непосредственно на сервере можно скопировать библиотеки в свой исходный код и развернуть их, как если бы они были частью приложения. В зависимости от числа имеющихся зависимостей и частоты их обновления этот метод может оказаться самым простым для получения рабочего развертывания.

Особенностью этого способа является то, что эти библиотеки должны точно соответствовать версии Python на сервере, в противном случае после развертывания возникнут непонятные ошибки. Однако так как версии Python в расширениях сайтов службы приложений полностью аналогичны тем, которые опубликованы на сайте python.org, вы легко можете получить совместимую версию для локальной разработки.

### <a name="avoiding-virtual-environments"></a>Отказ от виртуальных окружений

Хотя локальная работа в виртуальном окружении может помочь вам полноценно изучить нужные сайту зависимости, использовать виртуальные окружения в службе приложений не рекомендуется. Вместо этого просто установите библиотеки в основную папку Python и разверните их вместе с приложением, чтобы предотвратить конфликты зависимостей.
