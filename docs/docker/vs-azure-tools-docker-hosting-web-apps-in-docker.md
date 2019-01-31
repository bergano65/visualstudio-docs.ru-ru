---
title: Развертывание контейнера ASP.NET Docker в реестре контейнеров Azure (ACR) | Документация Майкрософт
description: Сведения об использовании средства Visual Studio для Docker для развертывания веб-приложения ASP.NET Core в реестре контейнеров
services: azure-container-service
documentationcenter: .net
author: mlearned
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.service: azure-container-service
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 05/21/2018
ms.author: mlearned
ms.openlocfilehash: 8ba7244ffc482c33409bc280617b60ce1e85b504
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140765"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio

## <a name="overview"></a>Обзор

Docker — это облегченная платформа контейнеров, чем-то похожая на виртуальную машину, которую можно использовать для размещения приложений и служб.
Это руководство покажет как с помощью Visual Studio публиковать контейнерные приложения в [реестре контейнеров Azure](https://azure.microsoft.com/services/container-registry).

Если у вас еще нет подписки Azure, [создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs), прежде чем начинать работу.

## <a name="prerequisites"></a>Предварительные требования

Для работы с этим руководством вам понадобится следующее:

* Установите последнюю версию [Visual Studio 2017](https://azure.microsoft.com/downloads/) с рабочей нагрузкой "ASP.NET и разработка веб-приложений"
* Установить [Docker для Windows](https://docs.docker.com/docker-for-windows/install/).

## <a name="1-create-an-aspnet-core-web-app"></a>1. Создание веб-приложения ASP.NET Core
Давайте создадим простое приложение ASP.NET Core, которое мы будем использоваться в этом руководстве.

[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]

## <a name="2-publish-your-container-to-azure-container-registry"></a>2. Опубликуйте контейнер в реестре контейнеров Azure
1. В **обозревателе решений** щелкните правой кнопкой проект и выберите **Опубликовать**.
2. В диалоговом окне целевой публикации выберите вкладку **Реестр контейнеров**.
3. Выберите **Создать реестр контейнеров Azure** и щелкните **Опубликовать**.
4. Заполните нужные значения в окне **Создать новый реестр контейнеров Azure**.

    | Параметр      | Рекомендуемое значение  | ОПИСАНИЕ                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-префикс** | Глобально уникальное имя | Имя, которое однозначно идентифицирует реестр контейнеров. |
    | **Подписка** | Выберите свою подписку | Подписка Azure, которую нужно использовать. |
    | **[Группа ресурсов](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Имя группы ресурсов, в которой создается реестр контейнеров. Чтобы создать группу ресурсов, выберите **Создать**.|
    | **[SKU](https://docs.microsoft.com/azure/container-registry/container-registry-skus)** | Стандартный | Уровень обслуживания в реестре контейнеров  |
    | **Расположение реестра** | Расположение рядом с вами | Выберите расположение в ближайшем [регионе](https://azure.microsoft.com/regions/) или в регионе, расположенном рядом с другими службами, которые будут использовать реестр контейнеров. |

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio](media/vs-azure-tools-docker-hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Нажмите кнопку **Создать**.

Теперь можно извлечь контейнер из реестра в любой узел, поддерживающий работу образов Docker, например [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-tutorial-deploy-app).