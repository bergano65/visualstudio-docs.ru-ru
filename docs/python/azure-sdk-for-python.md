---
title: Пакет Azure SDK для Python
description: Пакет SDK Azure для Python — это удобное средство для работы со службами Microsoft Azure из приложений Python на любой платформе.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 241c7c424f9ef670f16eead4fc400e375584f8c2
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057958"
---
# <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python

Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac OSX и Linux.

## <a name="installation"></a>Установка

Azure SDK устанавливается из [пакетов Python](https://pypi.python.org/pypi/azure).

Чтобы установить **последнюю стабильную версию** (с поддержкой Python 2.7 и 3.x), выполните следующую команду:

```command
pip install azure
```

Также вы можете воспользоваться [инструкцией по установке Python и пакета SDK](https://docs.microsoft.com/azure/python-how-to-install/), предложенной в документации по Azure.

## <a name="documentation"></a>Документация

Документацию можно найти на сайте [azure-sdk-for-python.readthedocs.org](https://docs.microsoft.com/en-us/python/azure/?view=azure-python).

В [Центре разработчиков для языка Python](http://azure.microsoft.com/develop/python/) также содержится ряд полезных ресурсов, в том числе руководства.

- Создание веб-приложений с помощью [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) и [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Хранилище BLOB-объектов](/azure/storage/storage-python-how-to-use-blob-storage)
- [Хранилище таблиц](/azure/storage/storage-python-how-to-use-table-storage)
- [Хранилище очередей](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Очереди служебной шины](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Разделы и подписки, связанные со служебной шиной Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Управление службами](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Для общедоступных интерфейсов API без документации хорошим источником информации будут модульные тесты, представленные в [репозитории пакетов SDK на портале GitHub](https://github.com/Azure/azure-sdk-for-python):

- [Модульные тесты хранилища](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Модульные тесты Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Модульные тесты управления службами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Модульные тесты управления ресурсами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Поддержка

Репозиторий Git для пакета SDK находится в каталоге [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Если при использовании пакета SDK у вас возникнут любые проблемы или вопросы, [оставьте в репозитории описание проблем](https://github.com/Azure/azure-sdk-for-python/issues).
