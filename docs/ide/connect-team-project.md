---
title: Подключение к проектам в Team Explorer
description: Сведения о том, как использовать Team Explorer в Visual Studio для взаимодействия с членами команды при разработке проектов и управлении ими.
ms.custom: SEO-VS-2020
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: fd482bd2225025b5cd8a14f0387e938626fad6d5
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006319"
---
# <a name="connect-to-projects-in-team-explorer"></a>Подключение к проектам в Team Explorer

::: moniker range="vs-2017"

Окно средства **Team Explorer** используется для координации усилий с другими членами команды при разработке проекта, а также для управления работой, назначенной вам, вашей команде или вашим командным проектам. **Team Explorer** обеспечивает подключение Visual Studio к репозиториям Git и GitHub, репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в [службах Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) или на локальном [сервере Azure DevOps](/azure/devops/index-all) (прежнее название TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

::: moniker-end

::: moniker range="vs-2019"

Вы можете использовать окно средства **Team Explorer** для координации усилий с другими членами команды при разработке проекта, а также для управления работой, назначенной вам, вашей команде или вашим командным проектам.

> [!IMPORTANT]
> В последнем выпуске Visual Studio 2019 [версии 16.8](/visualstudio/releases/2019/release-notes/) новый интерфейс управления версиями Git включен по умолчанию. Но если вы предпочитаете и дальше использовать Team Explorer, выберите **Средства** > **Параметры** > **Среда** > **Функции предварительной версии** и снимите флажок **Новый пользовательский интерфейс Git**. Дополнительные сведения см. в статье [Новый интерфейс в Visual Studio](git-with-visual-studio.md).

**Team Explorer** обеспечивает подключение Visual Studio к репозиториям Git и GitHub, репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в [службах Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) или на локальном [сервере Azure DevOps](/azure/devops/index-all) (прежнее название TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

::: moniker-end

![Домашняя страница Team Explorer в Visual Studio](media/team-explorer/team-explorer.png "Team Explorer — домашняя страница в Visual Studio.")

::: moniker range="vs-2017"

> [!TIP]
> Если при запуске Visual Studio окно **Team Explorer** не появляется, откройте его, выбрав команду **Вид** > **Team Explorer** в строке меню или воспользовавшись клавишами **CTRL**+ **&#92;** , **CTRL**+**M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Подключение к проекту или репозиторию

Подключение к проекту или репозиторию можно выполнить на странице **Подключение**.

![Страница подключения в Team Explorer](media/team-explorer/connect.png "Team Explorer — страница "Подключения" в Visual Studio.")

Подключение к проекту:

1. Откройте страницу **Подключение**, щелкнув значок **Управление подключениями**.

   ![Кнопка "Управление подключениями" в Team Explorer](media/team-explorer/manage-connections.png "Team Explorer — кнопка "Управление подключениями" в Visual Studio.")

1. На странице **Подключение** выберите **Управление подключениями** > **Подключение к проекту**.

   ![Подключение к проекту в Team Explorer](media/team-explorer/connect-project.png "Team Explorer — вариант "Подключение к проекту" в Visual Studio.")

> [!TIP]
> Если вы хотите открыть проект из репозитория, см. статью [Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md). Если вы хотите создать новый проект или добавить пользователей в существующий, ознакомьтесь со статьями [Создание проекта (Azure DevOps)](/azure/devops/organizations/projects/create-project) и [Добавление пользователей в проект или команду (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>См. также

- [Новый интерфейс Git в Visual Studio](git-with-visual-studio.md)
- [Учебник. Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md)
- [Справка по Team Explorer](reference/team-explorer-reference.md)
- [Подключение к проекту (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Устранение неполадок с подключением к проекту](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
