---
title: Развертывание & публикация решения SharePoint на локальном сайте SharePoint
titleSuffix: ''
description: Узнайте, как развертывать или публиковать решения SharePoint на локальном сервере SharePoint на компьютере разработчика.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22fe46e2876b14551637dd97712e1728816b020e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913695"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Развертывание и публикация решения SharePoint на локальном сайте SharePoint
  Решения SharePoint можно развертывать или публиковать на локальном сервере SharePoint на компьютере разработчика. Процесс развертывания копирует *wspный* файл на сервер SharePoint, устанавливает решение, а затем активирует компоненты. Процесс публикации копирует только файл *WSP* на сервер SharePoint и устанавливает его. Его необходимо активировать вручную, чтобы включить его в SharePoint.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Развертывание решения SharePoint на локальном сервере SharePoint

1. В **Обозреватель решений** выберите проект, который требуется развернуть.

2. В строке меню последовательно выберите **Сборка** и **Развернуть решение**.

     *WSP* -файл создается и устанавливается на локальном сервере SharePoint. Кроме того, функции активируются.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Публикация решения SharePoint на локальном сервере SharePoint

1. В **Обозреватель решений** откройте контекстное меню проекта SharePoint, который необходимо опубликовать, и выберите **опубликовать**.

2. В диалоговом окне **Публикация** выберите переключатель **опубликовать в файловой системе** .

3. В текстовом поле **целевое расположение** введите локальный путь, а затем нажмите кнопку **опубликовать** .

     Ход публикации отображается в окне **вывод** Visual Studio. По завершении процесса на локальном сервере SharePoint устанавливается файл решения (*WSP*). Однако он по-прежнему должен быть активирован для использования в SharePoint. Если файл решения уже существует, возникает ошибка и спрашивается, нужно ли перезаписать существующий файл. Сведения об обновлении пакета см. в разделе Обновление удаленных пакетов статьи [развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>См. также раздел
- [Развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Как настроить пакет решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Пошаговое руководство. Добавление и удаление компонентов и элементов в пакет с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
