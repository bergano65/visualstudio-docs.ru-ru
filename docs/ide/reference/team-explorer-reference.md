---
title: Справка по Team Explorer
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: 6a7c1e9d0f5e8b8ef48a033d58038818d2d620e5
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222978"
---
# <a name="team-explorer-reference"></a>Справка по Team Explorer

В этой статье приводятся ссылки на статьи по Azure DevOps, посвященные различным возможностям в **Team Explorer**.

Окно средства **Team Explorer** используется для координации усилий с другими членами команды при разработке проекта, а также для управления работой, назначенной вам, вашей команде или вашим командным проектам. **Team Explorer** обеспечивает подключение Visual Studio к репозиториям Git и GitHub, репозиториям системы управления версиями Team Foundation (TFVC), а также проектам, размещенным в [службах Azure DevOps](/azure/devops/user-guide/what-is-azure-devops-services) или на локальном [сервере Azure DevOps](/tfs/index) (прежнее название TFS). Можно управлять исходным кодом, рабочими элементами и сборками.

## <a name="home-page"></a>домашняя страница

После [подключения к проекту](../connect-team-project.md) в **Team Explorer** в разделе **Проект** будут доступны следующие ссылки:

- [Клонировать репозиторий](/azure/devops/repos/git/clone)
- [Веб-портал](/azure/devops/project/navigation/index)
- [Доска задач](/azure/devops/boards/sprints/task-board)

На **домашней** странице реализуются другие функции в зависимости от того, подключены ли вы к [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) или репозиторию [системы управления версиями Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview).

> [!TIP]
> Сравнение этих двух систем управления версиями см. в разделе [Выбор подходящей системы управления версиями для проекта (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Домашняя** страница при подключении к Git | **Домашняя** страница при подключении к TFVC |
| - | - |
| ![Домашняя страница Team Explorer при подключении к Git в Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Домашняя страница Team Explorer при подключении к TFVC в Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Страница "Изменения" (Git)

См. раздел [Сохранение работы с помощью фиксаций](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Страница "Ветвления" (Git)

См. раздел [Создание рабочих элементов в ветвях](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Страница "Запросы на включение внесенных изменений" (Git)

См. раздел [Проверка кода с помощью запросов на включение внесенных изменений](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Страница "Синхронизация" (Git)

См. раздел [Обновление кода с помощью команд fetch и pull](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Страница "Теги" (Git)

См. раздел [Работа с тегами Git](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Страница "Моя работа" (TFVC)

См. разделы [Приостановка/возобновление работы](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) и [Проверка кода](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Страница "Отложенные изменения" (TFVC)

См. разделы [Управление отложенными изменениями](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [Поиск наборов отложенных изменений](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) и [Разрешение конфликтов](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Страница "Обозреватель управления исходным кодом" (TFVC)

См. раздел [Добавление и просмотр файлов и папок](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>Страница "Рабочие элементы"

На странице **Рабочие элементы** можно просмотреть запросы [рабочих элементов](/azure/devops/boards/work-items/about-work-items). Пример

- [Добавление рабочих элементов](/azure/devops/boards/backlogs/add-work-items)
- [Вывод списка запросов и управление ими с помощью редактора запросов](/azure/devops/boards/queries/using-queries)
- [Упорядочение папок запросов и предоставление разрешения запроса](/azure/devops/boards/queries/set-query-permissions)
- [Открытие запроса в Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Открытие запроса в Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Отправка списка результатов запроса по электронной почте с помощью Outlook](/azure/devops/boards/queries/share-plans)
- [Создание отчетов из запроса в Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (только для TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> В Visual Studio 2019 представлена новая [система управления рабочими элементами](/azure/devops/boards/work-items/set-work-item-experience-vs). Дополнительные сведения о просмотре рабочих элементов в Visual Studio 2019 см. в статье [Просмотр и добавление рабочих элементов](/azure/devops/boards/work-items/view-add-work-items).

::: moniker-end

## <a name="builds-page"></a>Страница "Сборки"

На странице **Сборки** можно просмотреть определения сборки для проекта.

Пример

- [Создание конвейера сборки](/azure/devops/pipelines/tasks/index)
- [Просмотр сборок и управление ими](/azure/devops/pipelines/overview)
- [Управление очередью сборки](/azure/devops/pipelines/agents/pools-queues)
- [Установка инструментов непрерывной поставки для Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Настройка и выполнение непрерывной поставки для приложения](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Страница "Параметры"

На странице **Параметры** можно настроить административные функции для проектов или коллекции проектов. См. следующие статьи:

| Проект | Коллекция проектов | Другое |
| - | - | - |
| [Безопасность, членство в группе](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Безопасность, система управления версиями (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Области рабочих элементов](/azure/devops/organizations/settings/set-area-paths)<br/>[Итерации рабочих элементов](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Параметры портала](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Оповещения проекта](/azure/devops/notifications/howto-manage-team-notifications) | [Безопасность, членство в группе](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Система управления версиями (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Диспетчер шаблона процесса](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Глобальные параметры Git](/azure/devops/repos/git/git-config)<br/>[Параметры репозитория Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>См. также

- [Подключение к проектам в Team Explorer](../../ide/connect-team-project.md)