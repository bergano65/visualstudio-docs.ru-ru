---
title: Пакет Azure SDK для Python
description: Пакет SDK Azure для Python — это удобное средство для работы со службами Microsoft Azure из приложений Python на любой платформе.
ms.date: 10/10/2018
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
ms.openlocfilehash: b1b41fe707c751b5cd32706d1c27f707f964dff8
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100930"
---
# <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python

Пакет SDK Azure для Python — это удобное средство для работы со службами Microsoft Azure из приложений Windows, MacOS и Linux.

## <a name="installation"></a>Установка

Azure SDK устанавливается из [пакетов Python](https://pypi.python.org/pypi/azure).

Чтобы установить **последнюю стабильную версию** (с поддержкой Python 2.7 и 3.x), выполните следующую команду:

```command
pip install azure
```

Также вы можете воспользоваться [инструкцией по установке Python и пакета SDK](https://docs.microsoft.com/azure/python-how-to-install/), предложенной в документации по Azure.

## <a name="documentation"></a>Документация

В [Центре разработчиков для языка Python](https://docs.microsoft.com/python/azure/?view=azure-python) также содержится ряд полезных ресурсов, в том числе руководства.

- Создание веб-приложений в "Службе приложений Azure" в Linux (/azure/app-service/containers/quickstart-python).
- [Хранилище BLOB-объектов](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Хранилище таблиц](/azure/cosmos-db/table-storage-how-to-use-python)
- [Хранилище очередей](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Очереди служебной шины](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Разделы и подписки, связанные со служебной шиной](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Управление службами](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Для общедоступных интерфейсов API без документации хорошим источником информации будут модульные тесты, представленные в [репозитории пакетов SDK на портале GitHub](https://github.com/Azure/azure-sdk-for-python):

- [Модульные тесты хранилища](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Модульные тесты Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Модульные тесты управления службами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Поддержка

Репозиторий GitHub для пакета SDK находится в каталоге [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Если при использовании пакета SDK у вас возникнут любые проблемы или вопросы, [оставьте в репозитории описание проблем](https://github.com/Azure/azure-sdk-for-python/issues).
