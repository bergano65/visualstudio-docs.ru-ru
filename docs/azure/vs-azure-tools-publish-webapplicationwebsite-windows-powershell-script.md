---
title: Публикация веб-приложения с помощью сценария PowerShell
description: Узнайте, как опубликовать веб-проект на веб-сайте Azure. Этот сценарий создает необходимые ресурсы в подписке Azure, если они еще не созданы.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c487084a276be31730f1e268527f4c10a2f7b747
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398830"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (сценарий Windows PowerShell)
## <a name="syntax"></a>Синтаксис
Этот сценарий публикует веб-проект на веб-сайте Azure и создает необходимые ресурсы в подписке Azure, если они еще не созданы.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Конфигурация
Путь к файлу конфигурации JSON, содержащему подробные сведения о развертывании.

| Параметр | Значение по умолчанию |
| --- | --- |
| Aliases |нет |
| Необходим? |Да |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="subscriptionname"></a>Параметр SubscriptionName
Имя подписки Azure, в которой необходимо создать веб-сайт.

| Параметр | Значение по умолчанию |
| --- | --- |
| Aliases |нет |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="webdeploypackage"></a>Параметр WebDeployPackage
Путь к пакету веб-развертывания для публикации на веб-сайте. Этот пакет можно создать с помощью мастера «Публикация веб-сайта» в Visual Studio. Дополнительные сведения можно найти в статье [Начало работы с облачными службами Azure и ASP.NET](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Параметр | Значение по умолчанию |
| --- | --- |
| Aliases |нет |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="databaseserverpassword"></a>Параметр DatabaseServerPassword
Имя и пароль администратора базы данных SQL в Azure.

| Параметр | Значение по умолчанию |
| --- | --- |
| Aliases |нет |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |нет |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="sendhostmessagestooutput"></a>Параметр SendHostMessagesToOutput
Если установлено значение true, оправляет сообщения из сценария в поток вывода.

| Параметр | Значение по умолчанию |
| --- | --- |
| Aliases |нет |
| Необходим? |false |
| Положение |именованный |
| Значение по умолчанию |false |
| Принимать входные данные конвейера? |false |
| Принимать символы-шаблоны? |false |

## <a name="remarks"></a>Комментарии
Подробное описание того, как использовать сценарий для создания сред разработки и тестирования, см. в статье [Использование скриптов Windows PowerShell для публикации в среды разработки и тестирования](vs-azure-tools-publishing-using-powershell-scripts.md).

В файле конфигурации JSON указаны данные объектов, которые необходимо развернуть. Он содержит сведения, указанные при создании проекта, такие как имя веб-сайта и имя пользователя. Он также содержит сведения о базе данных, которую нужно подготовить (если она есть). В следующем коде показан пример файла конфигурации JSON.

```json
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
```

В файле конфигурации JSON можно изменить объекты, которые подлежат развертыванию. Раздел webSite является обязательным, а раздел database — необязательным.

## <a name="next-steps"></a>Дальнейшие шаги
Дополнительные сведения см. в разделе [Publish-WebApplicationVM (сценарий Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md).
