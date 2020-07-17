---
title: Подключение к проектам в Team Explorer
ms.date: 07/07/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: bddb3afb602416159c75a5be9923fce14c089fc2
ms.sourcegitcommit: 4d932000a0f7e79c9475fe66c02fe9addcd7e47a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86181057"
---
# <a name="connect-to-projects-in-team-explorer"></a>Подключение к проектам в Team Explorer

Окно средства **Team Explorer** используется для координации усилий с другими членами команды при разработке проекта, а также для управления работой, назначенной вам, вашей команде или вашим командным проектам. **Team Explorer** обеспечивает подключение Visual Studio к репозиториям Git и GitHub, репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в [службах Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) или на локальном [сервере Azure DevOps](/azure/devops/index-all) (прежнее название TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

![Домашняя страница Team Explorer в Visual Studio](media/team-explorer/team-explorer.png)

> [!TIP]
> Если при запуске Visual Studio окно **Team Explorer** не появляется, откройте его, выбрав команду **Вид** > **Team Explorer** в строке меню или воспользовавшись клавишами **CTRL**+ **&#92;** , **CTRL**+**M**.

## <a name="connect-to-a-project-or-repository"></a>Подключение к проекту или репозиторию

Подключение к проекту или репозиторию можно выполнить на странице **Подключение**.

![Страница подключения в Team Explorer](media/team-explorer/connect.png)

Подключение к проекту:

1. Откройте страницу **Подключение**, щелкнув значок **Управление подключениями**.

   ![Кнопка "Управление подключениями" в Team Explorer](media/team-explorer/manage-connections.png)

1. На странице **Подключение** выберите **Управление подключениями** > **Подключение к проекту**.

   ![Подключение к проекту в Team Explorer](media/team-explorer/connect-project.png)

> [!TIP]
> Если вы хотите открыть проект из репозитория, см. статью [Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md). Если вы хотите создать новый проект или добавить пользователей в существующий, ознакомьтесь со статьями [Создание проекта (Azure DevOps)](/azure/devops/organizations/projects/create-project) и [Добавление пользователей в проект или команду (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>См. также

- [Учебник. Открытие проекта из репозитория](../get-started/tutorial-open-project-from-repo.md)
- [Справка по Team Explorer](reference/team-explorer-reference.md)
- [Подключение к проекту (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Устранение неполадок с подключением к проекту](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops)
