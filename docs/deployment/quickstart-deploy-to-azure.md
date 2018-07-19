---
title: Публикация в службу приложений Azure
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 7761164182188366425a81518f3d0513361b6f19
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077848"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Публикация веб-приложения в службе приложений Azure, с помощью Visual Studio

Можно использовать **публикации** средство для публикации приложения ASP.NET, ASP.NET Core, Node.js и .NET Core в службе приложений Azure или Azure служба приложений в Linux (с помощью контейнеров). Для приложений Python, следуя инструкциям в [Python — публикация в службе приложений Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **публикации** (или используйте **построения** > **публикации** пункт меню).

    ![Команда публикации в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "выберите публикации")

1. Если ранее вы настроили все профили публикации **публикации** откроется панель, в какие вариантов выберите **создать новый профиль**.

1. В **выберите целевой объект публикации** диалоговом окне выберите **службы приложений**.

    ![Выберите службу приложений Azure](../deployment/media/quickstart-publish-azure.png "выберите службу приложений Azure")

1. Нажмите **Публиковать**. **Создать службу приложений** откроется диалоговое окно. Войдите, используя вы учетную запись Azure, при необходимости, а затем параметрам службы приложений по умолчанию заполните поля.

    ![Создание службы приложений](../deployment/media/quickstart-publish-settings-app-service.png "Создание службы приложений Azure")

1. Выберите **Создать**. Visual Studio развертывает приложение на службу приложений Azure и загружает веб-приложение в браузере. Свойства проекта **публикации** области отображается URL-адрес сайта и другие сведения.

    ![Панель свойств со сводкой профиля публикации](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>Следующие шаги

В этом кратком руководстве вы узнали, как использовать Visual Studio для создания профиля публикации для развертывания в Azure. Вы также можете настроить публикации профиля, импортировав параметры публикации из службы приложений Azure.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в Azure](tutorial-import-publish-settings-azure.md)
