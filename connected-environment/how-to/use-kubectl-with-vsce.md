---
title: Как использовать kubectl с подключенной средой | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883531"
---
# <a name="use-kubectl-with-a-connected-environment"></a>Использование `kubectl` с подключенной средой

Вы можете получить доступ к кластеру Kubernetes в подключенной среде и использовать существующие инструменты Kubernetes, например `kubectl`.

Запуск `vsce env create` или `vsce env select` автоматически добавит контекст конфигурации `kubectl`, поэтому kubectl уже должен быть подключен к кластеру VSCE Kubernetes. Примеры
- Подтвердите текущий контекст: `kubectl config current-context`
- Список всех доступных контекстов: `kubectl config get-contexts`. Кластер kubernetes, созданный VSCE, будет иметь примерно следующее название: "vsce-<guid>".
- Изменение контекста: `kubectl config use-context <context-name>`
- Просмотр панели мониторинга Kubernetes: запустите `kubectl proxy`, затем откройте в браузере адрес, который выводит эта команда (добавьте `/ui` к URL-адресу для перехода к панели мониторинга Kubernetes).
- Указание выполняющихся служб в пространстве VSCE по умолчанию с именем *mainline*: `kubectl get services --namespace=mainline`

