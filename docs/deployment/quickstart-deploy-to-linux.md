---
title: Публикация в службе приложений на Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 790e88edcd5d0d77e09cc349c82c242cd3da876d
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830727"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Публикация веб-приложения ASP.NET Core в службе приложений на Linux с помощью Visual Studio

Начиная с Visual Studio 2017 версии 15.7 вы можете публиковать приложения ASP.NET Core в службе приложений Azure для Linux (с использованием контейнеров) с помощью одного из следующих методов.

* Для непрерывного (или автоматического) развертывания приложений используйте Azure DevOps с [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Для однократного развертывания (или развертывания вручную) используйте средство **публикации** в Visual Studio, чтобы публиковать приложения ASP.NET Core в службе приложений для Linux (с помощью контейнеров).

В этой статье описывается использование средства **публикации** для однократного развертывания.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Публикация в службе приложений Azure в Linux

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда Опубликовать в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды Опубликовать")

1. Если ранее вы настроили какие-либо профили публикации, появится окно **Опубликовать**. Нажмите кнопку **Создать**.

1. В окне **Публикация** выберите **Azure**.

    ![Выбор целевого объекта публикации](../deployment/media/quickstart-publish-azure-new.png)

1. Выберите **Служба приложений Azure (Linux)** и нажмите кнопку **Далее**.

    ![Выбор службы приложений Azure в Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. При необходимости выполните вход с использованием своей учетной записи Azure. Выберите **Создание новой службы приложений Azure**.

    ![Ссылка для создания нового экземпляра службы приложений Azure](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. В диалоговом окне **Создание службы приложений Azure (Linux)** необходимо заполнить поля **Имя приложения**, **Группа ресурсов** и **План службы приложений**. Вы можете сохранить эти имена или изменить их. Когда все будет готово, щелкните **Создать**.

    ![Выбор службы приложений Azure](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. В диалоговом окне **Публикация** вновь созданный экземпляр выбирается автоматически. Когда все будет готово, нажмите кнопку **Готово**.

    ![Выбор службы приложений Azure](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Нажмите **Публиковать**. Visual Studio выполнит развертывание приложения в службе приложений Azure, после чего веб-приложение будет загружено в браузер. В панели **Опубликовать** для свойств проекта будут отображаться URL-адрес сайта и другие сведения.

    ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

На предыдущем шаге вы создали ресурсы Azure в группе ресурсов. Если вы не планируете использовать эти ресурсы в будущем, вы можете удалить их, удалив саму группу ресурсов.
В меню слева на портале Azure выберите **Группы ресурсов**, после чего щелкните **myResourceGroup**.
На странице группы ресурсов проверьте, действительно ли требуется удалить перечисленные ресурсы.
Выберите **Удалить**, введите **myResourceGroup** в текстовое поле, после чего щелкните **Удалить**.

## <a name="next-steps"></a>Следующие шаги

Из этого краткого руководства вы узнали, как использовать Visual Studio, чтобы создать профиль публикации для развертывания в службе приложений на Linux. Ознакомьтесь с дополнительными материалами, посвященными публикации в Linux с использованием Azure.

> [!div class="nextstepaction"]
> [Служба приложений Linux](/azure/app-service/containers/app-service-linux-intro)