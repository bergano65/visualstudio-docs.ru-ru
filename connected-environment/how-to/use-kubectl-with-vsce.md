---
title: Как использовать kubectl с подключенной средой | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Использование `kubectl` с подключенной средой

Вы можете получить доступ к кластеру Kubernetes в подключенной среде и использовать существующие инструменты Kubernetes, например `kubectl`.

Запуск `vsce env create` или `vsce env select` автоматически добавит контекст конфигурации `kubectl`, поэтому kubectl уже должен быть подключен к кластеру VSCE Kubernetes. Примеры
- Подтвердите текущий контекст: `kubectl config current-context`
- Список всех доступных контекстов: `kubectl config get-contexts`. Кластер kubernetes, созданный VSCE, будет иметь примерно следующее название: "vsce-<guid>".
- Изменение контекста: `kubectl config use-context <context-name>`
- Просмотр панели мониторинга Kubernetes: запустите `kubectl proxy`, затем откройте в браузере адрес, который выводит эта команда (добавьте `/ui` к URL-адресу для перехода к панели мониторинга Kubernetes).
- Указание выполняющихся служб в пространстве VSCE по умолчанию с именем *mainline*: `kubectl get services --namespace=mainline`

