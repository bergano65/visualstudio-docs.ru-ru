---
title: Развертывание контейнера Docker ASP.NET Core в Docker Hub | Документация Майкрософт
description: Сведения об использовании инструментов Visual Studio для работы с контейнерами с целью развертывания веб-приложения ASP.NET Core в Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: 267e0c1ed1ac3911aad2161f186bf4a482f069b6
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "71126025"
---
# <a name="deploy-to-docker-hub"></a>Развертывание в Docker Hub

Docker Hub предоставляет удобную службу размещения для репозиториев образов. Вы можете легко выполнить развертывание в Docker Hub вручную из Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Создание учетной записи Docker и репозитория Docker Hub

[Зарегистрируйте](https://hub.docker.com/signup) учетную запись Docker, если у вас ее еще нет.

Если у вас нет репозитория Docker Hub, создайте его в [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Публикация образа для одного проекта в Docker Hub

1. Щелкните узел проекта правой кнопкой мыши и выберите команду **Опубликовать...** . Появится экран с вариантами развертывания.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. В разделе **Выберите целевой объект публикации** выберите **Реестр контейнеров**, а затем выберите **Docker Hub**. Появится диалоговое окно **Docker Hub**.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Если вы подключаетесь к собственному репозиторию (а не репозиторию организации), оставьте флажок **Опубликовать в личном репозитории** установленным. Если репозиторий принадлежит организации, снимите этот флажок и введите название организации. Введите имя пользователя и пароль учетной записи Docker с разрешениями на доступ к репозиторию, к которому вы подключаетесь, а затем нажмите кнопку **Сохранить**.  

   Visual Studio попытается развернуть образ в Docker Hub.  В случае успеха появится экран **Публикация** с URL-адресом образа репозитория, тегом образа, репозиторием и конфигурацией сборки (например, **Выпуск**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Вы можете обновить образ в любое время, нажав кнопку **Опубликовать** на этой странице.  Кроме того, можно изменить или удалить профиль с помощью ссылок под URL-адресом.

## <a name="next-steps"></a>Следующие шаги

Выполните публикацию в [Реестре контейнеров Azure](/azure/container-registry/) согласно инструкциям в статье [Развертывание в Реестр контейнеров Azure](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

Настройте непрерывную интеграцию и поставку (CI/CD) с помощью [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>См. также

[Развертывание в Службе приложений Azure](deploy-app-service.md)
[Инструменты Visual Studio для работы с контейнерами](/visualstudio/containers/).