---
title: Настройка узла Docker с помощью VirtualBox | Документация Майкрософт
description: Пошаговые инструкции по настройке экземпляра Docker по умолчанию с помощью машины Docker и VirtualBox.
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140725"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>Настройка узла Docker с помощью VirtualBox
## <a name="overview"></a>Обзор
В этой статье приводятся инструкции по настройке экземпляра Docker по умолчанию с помощью машины Docker и VirtualBox.
При использовании [Docker для Windows](https://www.docker.com/products/docker-desktop) эта настройка не требуется.

## <a name="prerequisites"></a>Предварительные требования
Должны быть установлены следующие средства.

* [Docker Toolbox](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Настройка клиента Docker с помощью Windows PowerShell
Чтобы настроить клиент Docker, просто откройте Windows PowerShell и выполните указанные ниже действия:

1. Создайте экземпляр узла Docker по умолчанию.

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. Убедитесь в том, что экземпляр по умолчанию настроен и выполняется. (Должен быть запущен экземпляр с именем default.

    ```PowerShell
    docker-machine ls
    ```

    ![Вывод: docker-machine ls](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. Задайте экземпляр по умолчанию в качестве текущего узла и настройте оболочку.

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. Отобразите активные контейнеры Docker. Список должен быть пустым.

    ```PowerShell
    docker ps
    ```

    ![Вывод: docker ps](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> Каждый раз, когда перезагружается компьютер разработки, необходимо перезапускать локальный узел Docker.
> Для этого выполните в командной строке следующую команду: `docker-machine start default`.
