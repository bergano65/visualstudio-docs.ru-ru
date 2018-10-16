---
title: Публикация в службе приложений на платформе Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341752"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Публикация приложения ASP.NET Core в службе приложений на платформе Linux с помощью Visual Studio

Можно использовать **публикации** , которая позволяет публиковать приложения ASP.NET Core в службе приложений Azure на платформе Linux.

Развертывание в службе приложений в Linux с использованием **публикации** для запуска этого средства Visual Studio 2017 версии 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Публикация в службе приложений на платформе Linux

1. В обозревателе решений щелкните правой кнопкой мыши проект и выберите **публикации** (или используйте **построения** > **публикации** пункт меню).

    ![Команда публикации в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "выберите публикации")

1. Если ранее вы настроили все профили публикации **публикации** откроется панель, в какие вариантов выберите **создать новый профиль**.

1. В **выберите целевой объект публикации** диалоговом окне выберите **служба приложений в Linux**.

    ![Выберите службу приложений Azure](../deployment/media/quickstart-publish-linux.png "выберите службу приложений Azure")

1. Нажмите **Публиковать**. **Создать службу приложений** откроется диалоговое окно. Войдите, используя вы учетную запись Azure, при необходимости, а затем параметрам службы приложений по умолчанию заполните поля.

    ![Создание службы приложений](../deployment/media/quickstart-publish-settings-app-service-linux.png "Создание службы приложений Azure")

1. Выберите **Создать**. Visual Studio развертывает приложение на службу приложений Azure и загружает веб-приложение в браузере. Свойства проекта **публикации** области отображается URL-адрес сайта и другие сведения.

    ![Панель свойств со сводкой профиля публикации](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

На предыдущих шагах вы создали ресурсы Azure в группе ресурсов. Если вам не понадобятся в будущем эти ресурсы требуются, их можно удалить, удалив группу ресурсов.
В меню слева на портале Azure выберите **групп ресурсов** , а затем выберите **myResourceGroup**.
На странице группы ресурсов убедитесь, что перечислены ресурсы, которые требуется удалить.
Выберите **удалить**, тип **myResourceGroup** в текстовое поле, а затем выберите **удалить**.

## <a name="next-steps"></a>Следующие шаги

В этом кратком руководстве вы узнали, как использовать Visual Studio для создания профиля публикации для развертывания в службе приложений на платформе Linux. Дополнительные сведения о публикации в Linux с помощью Azure можно.

> [!div class="nextstepaction"]
> [Служба приложений Linux](/azure/app-service/containers/app-service-linux-intro)
