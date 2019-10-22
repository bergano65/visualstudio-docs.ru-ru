---
title: Развертывание контейнера Docker для ASP.NET в реестре ACR
description: Сведения об использовании инструментов Visual Studio для работы с контейнерами с целью развертывания веб-приложения ASP.NET Core в реестре контейнеров
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: b3b012bfe3b9fc359a8c9688c52aa5bfc27fd2c7
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126145"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio

## <a name="overview"></a>Обзор

Docker — это облегченная платформа контейнеров, чем-то похожая на виртуальную машину, которую можно использовать для размещения приложений и служб.
Это руководство покажет как с помощью Visual Studio публиковать контейнерные приложения в [реестре контейнеров Azure](https://azure.microsoft.com/services/container-registry).

Если у вас еще нет подписки Azure, [создайте бесплатную учетную запись Azure](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs), прежде чем начинать работу.

## <a name="prerequisites"></a>Предварительные требования

Для работы с этим руководством вам понадобится следующее:

::: moniker range="vs-2017"
* Установите последнюю версию [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с рабочей нагрузкой "ASP.NET и разработка веб-приложений"
::: moniker-end
::: moniker range=">=vs-2019"
* Установите последнюю версию [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой "ASP.NET и разработка веб-приложений"
::: moniker-end
* Установить [Docker для Windows](https://docs.docker.com/docker-for-windows/install/).

## <a name="create-an-aspnet-core-web-app"></a>Создание веб-приложения ASP.NET Core
Давайте создадим простое приложение ASP.NET Core, которое мы будем использоваться в этом руководстве.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>Опубликуйте контейнер в реестре контейнеров Azure
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

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Нажмите кнопку **Создать**.

Теперь можно извлечь контейнер из реестра в любой узел, поддерживающий работу образов Docker, например [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-tutorial-deploy-app).
