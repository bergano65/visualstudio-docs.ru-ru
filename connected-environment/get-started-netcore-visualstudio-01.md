---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке с Visual Studio — шаг 1 — установка средств | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 64aa0b322c777baa78da5bf86cb1220a47128d93
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Начало работы в подключенной среде с .NET Core и Visual Studio

В этом руководстве мы научимся:

1. создавать оптимизированную для разработки среду на базе Kubernetes в Azure;
1. последовательно разрабатывать код в контейнерах с помощью Visual Studio;
1. независимо разрабатывать две отдельные службы и использовать обнаружение службы DNS в Kubernetes для вызова другой службы;
1. продуктивно разрабатывать и тестировать свой код в коллективной среде.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Установка интерфейса командной строки в подключенной среде
Для подключенной среды требуется минимальная настройка локального компьютера. Большая часть конфигураций среды разработки хранится в облаке и используется совместно с другими пользователями.

1. Загрузите и запустите [установщик интерфейса командной строки для подключенной среды](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Инструменты отладки Kubernetes
Конечно, вы можете использовать интерфейс командной строки для подключенных сред в качестве отдельного инструмента, но разработчикам .NET Core и Node.js в **VS Code** или **Visual Studio** доступны широкие возможности, например **отладка Kubernetes**.

### <a name="visual-studio-debugging"></a>Отладка в Visual Studio 
1. Установите последнюю версию [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. В установщике Visual Studio выберите следующую рабочую нагрузку:
    * ASP.NET и веб-разработка
1. Установка [расширения Visual Studio для подключенной среды](https://aka.ms/get-vsce-visualstudio)

Теперь мы готовы создать веб-приложение ASP.NET с помощью Visual Studio.

> [!div class="nextstepaction"]
> [Создание веб-приложения ASP.NET](get-started-netcore-visualstudio-02.md)
