---
title: "Пакет Azure SDK для Python | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ca0318e84c3bb8787b1a499f83d11389699817f2
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python

Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac OSX и Linux.

## <a name="installation"></a>Установка

Azure SDK устанавливается из [пакетов Python](https://pypi.python.org/pypi/azure).

Чтобы установить **последнюю стабильную версию** (поддерживает Python 2.7 и 3.3 +), выполните следующие действия.

```bash
pip install azure
```

Также вы можете воспользоваться [инструкцией по установке Python и пакета SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/), предложенной в документации по Azure.

## <a name="documentation"></a>Документация

Документацию можно найти на сайте [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

[Раздел пакета Azure SDK в Центре разработчиков для языка Python](http://azure.microsoft.com/develop/python/) также имеет ряд полезных ресурсов, включая учебные материалы.

  - Создание веб-приложений с помощью [Django](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) и [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
  - [Хранилище BLOB-объектов](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [Хранилище таблиц](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [Хранилище очередей](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [Очереди служебной шины](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [Разделы и подписки, связанные со служебной шиной Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [Управление службами](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Для общедоступных интерфейсов API без документации хорошим источником информации будут модульные тесты, представленные в [репозитории GitHub по пакету SDK](https://github.com/Azure/azure-sdk-for-python).

- [Модульные тесты хранилища](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Модульные тесты Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Модульные тесты управления службами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Модульные тесты управления ресурсами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Поддержка

Репозиторий для пакета SDK находится по адресу [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Если при использовании пакета SDK у вас возникнут любые проблемы или вопросы, [оставьте в репозитории описание проблем](https://github.com/Azure/azure-sdk-for-python/issues).
