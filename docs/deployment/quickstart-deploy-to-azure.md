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
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341694"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Публикация веб-приложения в службе приложений Azure с помощью Visual Studio

С помощью инструмента **Опубликовать** вы можете публиковать приложения ASP.NET, ASP.NET Core, Node.js и .NET Core в службе приложений Azure или службе приложений Azure для Linux (с использованием контейнеров). Для приложений Python выполните инструкции, приведенные в статье [Python: публикация в службе приложений Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Публикация в службу приложений Azure

1. В обозревателе решений щелкните проект правой кнопкой мыши и выберите пункт **Опубликовать** (или воспользуйтесь командой меню **Сборка** > **Опубликовать**).

    ![Команда "Опубликовать" в контекстном меню проекта в обозревателе решений](../deployment/media/quickstart-publish.png "Выбор команды \"Опубликовать\"")

1. Если ранее вы настроили какие-либо профили публикации, появится панель **Опубликовать**. В этом случае выберите команду **Создать новый профиль**.

1. В открывшемся диалоговом окне **Выбрать целевой объект для публикации** укажите **Служба приложений**.

    ![Выбор службы приложений Azure](../deployment/media/quickstart-publish-azure.png "Выбор службы приложений Azure")

1. Нажмите **Публиковать**. Появится диалоговое окно **Создание службы приложений**. При необходимости выполните вход с использованием учетной записи Azure, после чего в поля будут занесены параметры службы приложений по умолчанию.

    ![Создание службы приложений](../deployment/media/quickstart-publish-settings-app-service.png "Создание службы приложений Azure")

1. Выберите **Создать**. Visual Studio выполнит развертывание приложения в службе приложений Azure, после чего веб-приложение будет загружено в браузер. В панели **Опубликовать** для свойств проекта будут отображаться URL-адрес сайта и другие сведения.

    ![Панель свойств публикации с обзором профиля](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

На предыдущих шагах вы создали ресурсы Azure в группе ресурсов. Если вы не планируете использовать эти ресурсы в будущем, вы можете удалить их, удалив саму группу ресурсов.
В меню слева на портале Azure выберите **Группы ресурсов**, после чего щелкните **myResourceGroup**.
На странице группы ресурсов проверьте, действительно ли требуется удалить перечисленные ресурсы.
Выберите **Удалить**, введите **myResourceGroup** в текстовое поле, после чего щелкните **Удалить**.

## <a name="next-steps"></a>Следующие шаги

Из этого краткого руководства вы узнали, как использовать Visual Studio, чтобы создать профиль публикации для развертывания в Azure. Кроме того, вы можете настроить профиль публикации путем импорта параметров публикации из службы приложений Azure.

> [!div class="nextstepaction"]
> [Импорт параметров публикации и развертывание в Azure](tutorial-import-publish-settings-azure.md)
