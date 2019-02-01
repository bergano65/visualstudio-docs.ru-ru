---
title: Настройка именованных учетных данных для аутентификации | Документация Майкрософт
description: Узнайте, как указать учетные данные, которые Visual Studio сможет использовать для проверки подлинности запросов к Azure, чтобы опубликовать приложение из Visual Studio в Azure или отслеживать существующую облачную службу.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev15
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 2b8b3ab9bc5bd61a4abc983826cc97c3d032e824
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140885"
---
# <a name="set-up-named-authentication-credentials"></a>Настройка учетных данных для проверки подлинности

Для публикации приложения в Azure, наблюдения за имеющейся облачной службой или аутентификации запросов в Azure Visual Studio требуются учетные данные, а именно идентификатор подписки Azure и допустимый сертификат X.509 версии 3 с ключом не менее 2048 бит. Представьте эти учетные данные одним из следующих методов:

- В Visual Studio выберите **Просмотр > Обозреватель серверов**, щелкните правой кнопкой мыши узел **Azure**, выберите **Connect to Microsoft Azure Subscription** (Подключение к подписке Microsoft Azure), а затем выполните вход.
- Создайте файл подписки (`.publishsettings`), который содержит открытый ключ для сертификата. Как описано в этой статье, файл подписки может содержать учетные данные нескольких подписок.

Примечание. Эти учетные данные отличаются от учетных данных, используемых для аутентификации запросов в службах хранилища Azure.

## <a name="create-a-subscription-file"></a>Создание файла подписки

В обозревателе сервера щелкните правой кнопкой мыши узел **Azure**, а затем выберите **Manage and Filter Subscriptions** (Управление подписками и их фильтрация). Выберите вкладку **Сертификаты**, а затем выполните одно из следующих действий:

- Выберите **Импорт**, чтобы открыть диалоговое окно **Импорт подписок Microsoft Azure**. Выберите ссылку **Загрузки файла подписки** и сохраните скачанный файл во временное место в браузере. В диалоговом окне перейдите к папке скачивания, а затем импортируйте ее для использования при аутентификации.
- Выберите активную подписку, затем диалоговое окно **Редактирование**, в котором можно изменить существующую подписку для использования при аутентификации.
- Выберите **Создать**, чтобы открыть диалоговое окно **Создать подписку** и введите необходимые сведения. Чтобы отправить сертификат в облачную службу, указанную в диалоговом окне входа на портал Azure, перейдите к облачной службе, выберите **Параметры > Сертификаты управления**, щелкните **Отправить**, а затем укажите путь к файлу `.cer`.

Если вы хотите создать сертификат самостоятельно, следуйте инструкциям в статье [Общие сведения о сертификатах для облачных служб Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) и вручную передайте сертификат на [портал Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Следующие шаги

- [Документация по веб-приложениям](https://docs.microsoft.com/azure/app-service/)
- [Развертывание приложения в службе приложений Azure](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git)
- [Развертывание веб-заданий с помощью Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Создание и развертывание облачной службы](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)