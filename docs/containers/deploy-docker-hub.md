---
title: Развертывание контейнера Docker ASP.NET Core в Docker Hub | Документация Майкрософт
description: Сведения об использовании инструментов Visual Studio для работы с контейнерами с целью развертывания веб-приложения ASP.NET Core в Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 5bbdbffa9de9ac7789495249d3e7bfb0a8d65377
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2020
ms.locfileid: "91829901"
---
# <a name="deploy-to-docker-hub"></a>Развертывание в Docker Hub

Docker Hub предоставляет удобную службу размещения для репозиториев образов. Вы можете легко выполнить развертывание в Docker Hub вручную из Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Создание учетной записи Docker и репозитория Docker Hub

[Зарегистрируйте](https://hub.docker.com/signup) учетную запись Docker, если у вас ее еще нет.

Если у вас нет репозитория Docker Hub, создайте его в [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Публикация образа для одного проекта в Docker Hub

1. Щелкните узел проекта правой кнопкой мыши и выберите команду **Опубликовать...** . Появится экран с вариантами развертывания.

   ![Снимок экрана параметров развертывания](media/container-tools/vs-2019/docker-container-registry.png)

1. Выберите **Реестр контейнеров Docker**, а затем выберите **Docker Hub**.

   ![Снимок экрана диалогового окна публикации — выбор Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Введите учетные данные Docker.

   ![Снимок экрана диалогового окна Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Если вы подключаетесь к собственному репозиторию (а не репозиторию организации), оставьте флажок **Опубликовать в личном репозитории** установленным. Если репозиторий принадлежит организации, снимите этот флажок и введите название организации. Введите имя пользователя и пароль учетной записи Docker с разрешениями на доступ к репозиторию, к которому вы подключаетесь, а затем нажмите кнопку **Сохранить**.

   Visual Studio попытается развернуть образ в Docker Hub.  В случае успеха появится экран **Публикация** с URL-адресом образа репозитория, тегом образа, репозиторием и конфигурацией сборки (например, **Выпуск**).

   ![Снимок экрана "Публикация"](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Вы можете обновить образ в любое время, нажав кнопку **Опубликовать** на этой странице.  Кроме того, можно изменить или удалить профиль с помощью ссылок под URL-адресом.

## <a name="next-steps"></a>Следующие шаги

Выполните публикацию в [Реестре контейнеров Azure](/azure/container-registry/) согласно инструкциям в статье [Развертывание в Реестр контейнеров Azure](hosting-web-apps-in-docker.md).

Настройте непрерывную интеграцию и поставку (CI/CD) с помощью [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).

## <a name="see-also"></a>См. также

[Развертывание в Службе приложений Azure](deploy-app-service.md)
[Инструменты Visual Studio для работы с контейнерами](./index.yml).