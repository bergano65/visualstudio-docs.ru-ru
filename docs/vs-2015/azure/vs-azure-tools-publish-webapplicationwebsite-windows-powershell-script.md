---
title: Publish-WebApplicationWebSite (сценарий Windows PowerShell) | Документация Майкрософт
description: Узнайте, как для публикации веб-проекта в веб-приложения Azure. Этот сценарий создает необходимые ресурсы в подписке Azure, если они не существуют.
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002894"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (скрипт Windows PowerShell)
## <a name="syntax"></a>Синтаксис
Публикует веб-проекта в веб-приложения Azure. Сценарий создает необходимые ресурсы в подписке Azure, если они не существуют.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Конфигурация
Путь к файлу конфигурации JSON, описывающий сведения о развертывании.

| Параметр | Значение по умолчанию |
| --- | --- |
| Псевдонимы |Нет |
| Обязательный? |true |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="subscriptionname"></a>SubscriptionName
Имя подписки Azure, который вы хотите создать веб-сайт в.

| Параметр | Значение по умолчанию |
| --- | --- |
| Псевдонимы |Нет |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
Путь к веб-пакета развертывания для публикации на веб-сайт. Этот пакет можно создать с помощью мастера публикации веб-сайта в Visual Studio. Дополнительные сведения см. в разделе [приступить к работе с облачными службами Azure и ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Параметр | Значение по умолчанию |
| --- | --- |
| Псевдонимы |Нет |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Имя пользователя и пароль для базы данных SQL Azure.

| Параметр | Значение по умолчанию |
| --- | --- |
| Псевдонимы |Нет |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Если значение равно true, оправляет сообщения из сценария в поток вывода.

| Параметр | Значение по умолчанию |
| --- | --- |
| Псевдонимы |Нет |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |False |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="remarks"></a>Примечания
Подробное описание того, как использовать сценарий для создания сред разработки и тестирования, см. в разделе [с помощью скриптов Windows PowerShell для публикации в средах разработки и тестирования](vs-azure-tools-publishing-using-powershell-scripts.md).

Файл конфигурации JSON указывает подробные сведения о возможностях для развертывания. Он содержит сведения, что вы указали при создании проекта, например имя и имя пользователя для веб-сайта. Она также включает базу данных для подготовки, если таковые имеются. Ниже приведен пример файла конфигурации JSON:

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

Можно изменить файл конфигурации JSON для подлежат развертыванию. Раздел webSite является обязательным, но раздел базы данных является необязательным.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в разделе [Publish-WebApplicationVM (сценарий Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)

