---
title: Публикация в службу приложений Azure
description: Узнайте о методах публикации приложений ASP.NET, ASP.NET Core, Node.js и .NET Core в службе приложений Azure или службе приложений Azure для Linux.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: 11e655adcfecb9ab63479275b64873fa4c9e6d0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927448"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Публикация веб-приложения в службе приложений Azure с помощью Visual Studio

Приложения ASP.NET, ASP.NET Core, Node.js и .NET Core можно публиковать в службе приложений Azure или службе приложений Azure для Linux (с использованием контейнеров) одним из следующих методов.

* Для непрерывного (или автоматического) развертывания приложений используйте Azure DevOps с [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Для однократного развертывания (или развертывания вручную) используйте средство **публикации** в Visual Studio, чтобы развертывать приложения ASP.NET, ASP.NET Core, Node.js и .NET Core в службе приложений Azure или [службе приложений для Linux](../deployment/quickstart-deploy-to-linux.md) (с помощью контейнеров). Для приложений Python выполните инструкции, приведенные в статье [Python: публикация в службе приложений Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

В этой статье описывается использование средства **публикации** для однократного развертывания.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Публикация в службу приложений Azure на платформе Windows

1. В Обозревателе решений щелкните узел проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда Опубликовать в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды Опубликовать")

1. Если ранее вы настроили какие-либо профили публикации, появится окно **Опубликовать**. Нажмите кнопку **Создать**.

1. В окне **Публикация** выберите **Azure**.

    ![Выбор целевого объекта публикации](../deployment/media/quickstart-publish-azure-new.png)

1. Выберите **Служба приложений Azure (Windows)** и нажмите кнопку **Далее**.

    ![Выбор службы приложений Azure в Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. При необходимости выполните вход с использованием своей учетной записи Azure. Выберите **Создание новой службы приложений Azure**.

    ![Ссылка для создания нового экземпляра службы приложений Azure](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. В диалоговом окне **Создание службы приложений Azure (Windows)** необходимо заполнить поля **Имя приложения**, **Группа ресурсов** и **План службы приложений**. Вы можете сохранить эти имена или изменить их. Когда все будет готово, щелкните **Создать**.

    ![Снимок экрана: диалоговое окно Create Azure App Service (Windows) (Создание службы приложений Azure" (Windows)) с заполненными полями "Имя", "Подписка", "Группа ресурсов" и "План размещения".](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. В диалоговом окне **Публикация** вновь созданный экземпляр выбирается автоматически. По завершении нажмите кнопку **Готово**.

    ![Снимок экрана: окно "Публикация", доступ к которому осуществлен из Обозревателя решений Visual Studio. Azure выбран в качестве целевого объекта публикации.](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Нажмите **Публиковать**. Visual Studio выполнит развертывание приложения в службе приложений Azure, после чего веб-приложение будет загружено в браузер. В панели **Опубликовать** для свойств проекта будут отображаться URL-адрес сайта и другие сведения.

    ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

На предыдущем шаге вы создали ресурсы Azure в группе ресурсов. Если вы не планируете использовать эти ресурсы в будущем, вы можете удалить их, удалив саму группу ресурсов.
В меню слева на портале Azure выберите **Группы ресурсов**, после чего щелкните **myResourceGroup**.
На странице группы ресурсов проверьте, действительно ли требуется удалить перечисленные ресурсы.
Выберите **Удалить**, введите **myResourceGroup** в текстовое поле, после чего щелкните **Удалить**.

## <a name="next-steps"></a>Следующие шаги

Из этого краткого руководства вы узнали, как использовать Visual Studio, чтобы создать профиль публикации для развертывания в Azure. Кроме того, вы можете настроить профиль публикации путем импорта параметров публикации из службы приложений Azure.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в Azure](tutorial-import-publish-settings-azure.md)
