---
title: Публикация приложения Python в Службе приложений Azure
description: Способы публикации приложения Python в Службе приложений Azure.
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
ms.openlocfilehash: 050b98f663a1db6bde6d32342b094fe454046283
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459664"
---
# <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

Сейчас Python поддерживается в Службе приложений Azure для Linux. Вы можете публиковать приложения с помощью [развертывания Git](#publish-to-app-service-on-linux-using-git-deploy) и [контейнеров](#publish-to-app-service-on-linux-using-containers), как описано в этой статье.

> [!Note]
> Средства поддержки Python в Службе приложений Azure для Windows официально признаны нерекомендуемыми. Поэтому команду **публикации** в Visual Studio официально поддерживают только [целевые службы IIS](#publish-to-iis), а удаленная отладка в Службе приложений Azure официально не поддерживается.
>
> Но функция [публикации в Службе приложений в Windows](publish-to-app-service-windows.md) по-прежнему работает, так как расширения Python для Службы приложений в Windows еще доступны, но не будут обслуживаться или обновляться.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Публикация в Службе приложений в Linux с помощью развертывания Git

При развертывании с помощью Git Служба приложений для Linux подключается к конкретной ветви репозитория Git. Если зафиксировать код в этой ветви, он автоматически будет развернут в Службе приложений. Также Служба приложений автоматически устанавливает все зависимости, перечисленные в файле *requirements.txt*. В этом случае Служба приложений на Linux выполняет код в предварительно настроенном образе контейнера, который использует веб-сервер Gunicorn. Сейчас доступна предварительная версия этой службы, не предназначенная для использования в рабочей среде.

Дополнительные сведения см. в следующих статьях документации по Azure:

- В [кратком руководстве по созданию веб-приложения Python в Службе приложений](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) приведено пошаговое описание развертывания из локального репозитория Git на примере приложения Flask.
- В руководстве по [настройке приложения Python](/azure/app-service/containers/how-to-configure-python) описаны характеристики Службы приложений для контейнеров Linux и объясняется, как настроить команду запуска Gunicorn для приложения.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Публикация в Службе приложений на Linux с помощью контейнеров

Вы можете не использовать готовый контейнер со Службой приложений в Linux, а указать собственный. Такой способ позволяет выбрать используемые веб-серверы и настроить поведение контейнера.

Есть два способа создания, администрирования и отправки контейнеров:

- С помощью Visual Studio Code и расширения Docker, как описано в [руководстве по развертыванию Python с помощью контейнеров Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Даже если вы не используете Visual Studio Code, ознакомьтесь со статьей. Она содержит полезные сведения о том, как создать образы контейнеров для приложений Flask и Django с помощью готовых веб-серверов uwsgi и nginx. Этот же контейнер можно потом развернуть с помощью Azure CLI.

- С помощью командной строки и Azure CLI, как описано в [руководстве по применению пользовательского образа Docker](/azure/app-service/containers/tutorial-custom-docker-image) в документации по Azure. Это общее руководство, оно не предназначено специально для Python.

## <a name="publish-to-iis"></a>Публикация в службах IIS

Можно опубликовать приложение из Visual Studio на виртуальных машинах Windows или на другом компьютере с поддержкой IIS, используя команду **Опубликовать**. При использовании служб IIS создайте или измените файл *web.config*, в котором для IIS указывается путь к интерпретатору Python, в приложении. Дополнительные сведения см. в статье [Configure Python web apps for IIS](configure-web-apps-for-iis-windows.md) (Настройка веб-приложений Python для IIS).
