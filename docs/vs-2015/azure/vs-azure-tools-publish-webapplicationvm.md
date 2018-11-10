---
title: Publish-WebApplicationVM | Документация Майкрософт
description: Сведения о развертывании веб-приложения к виртуальной машине. Этот сценарий создает необходимые ресурсы в подписке Azure, если они не существуют.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003004"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (скрипт Windows PowerShell)
Развертывает веб-приложения к виртуальной машине. Сценарий создает необходимые ресурсы в подписке Azure, если они не существуют.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Конфигурация
Путь к файлу конфигурации JSON, описывающий сведения о развертывании.

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |true |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="subscriptionname"></a>SubscriptionName
Имя подписки Azure, в котором вы хотите создать виртуальную машину.

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Используется первая подписка в файле подписок |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Путь к веб-пакета развертывания для публикации для виртуальной машины. Этот пакет можно создать с помощью мастера публикации веб-сайта в Visual Studio. См. в разделе [как: Создание веб-пакета развертывания в Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Если значение равно true, разрешите использование сертификатов, которые не подписаны доверенным корневым центром сертификации.

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |False |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="vmpassword"></a>VMPassword
Учетные данные для учетной записи виртуальной машины. Пример: - VMPassword @{Name = «admin»; Пароль = «password»}

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Учетные данные для базы данных SQL Azure. Пример: - DatabaseServerPassword @{Name = «admin»; Пароль = «password»}

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |Нет |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Если значение равно true, оправляет сообщения из сценария в поток вывода.

| Псевдонимы | Нет |
| --- | --- |
| Обязательный? |False |
| Положение |именованные |
| Значение по умолчанию |False |
| Принимает входные данные конвейера? |False |
| Принимать подстановочные знаки? |False |

## <a name="remarks"></a>Примечания
Подробное описание того, как использовать сценарий для создания сред разработки и тестирования, см. в разделе [с помощью скриптов Windows PowerShell для публикации в средах разработки и тестирования](vs-azure-tools-publishing-using-powershell-scripts.md).

Файл конфигурации JSON указывает подробные сведения о возможностях для развертывания. Он включает в себя сведения, которые вы указали при создании проекта, например имя, территориальная группа, образ виртуального жесткого диска и размер виртуальной машины. Также включает конечные точки виртуальной машины, подготавливаемые базы данных, если таковые имеются и параметры веб-развертывания. Ниже приведен пример файла конфигурации JSON:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Можно изменить файл конфигурации JSON для подлежат подготовке. Виртуальная машина и облачная служба являются обязательными, но раздел базы данных является необязательным.

