---
title: Добавление службы хранилища Azure с помощью Подключенные службы
description: Добавление хранилища Azure в приложение с помощью диалогового окна "Добавление подключенных служб" в Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 3acb009d27a9fa47f890235f6957d1f29ed2f4a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916697"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Добавление хранилища Azure с использованием подключенных служб Visual Studio
В Visual Studio с помощью диалогового окна **Add Connected Services** (Добавление подключенных служб) можно подключить любое из следующих хранилищ Azure:

- облачную службу C#;
- серверную мобильную службу .NET;
- веб-сайт или службу ASP.NET;
- службу ASP.NET Core;
- службу веб-заданий Azure.

Подключенные службы добавляют необходимые ссылки и код подключения в проект и вносят соответствующие изменения в файлы конфигурации.

По завершении в диалоговом окне **Add Connected Services** (Добавление подключенных служб) автоматически отображается документация с подробным описанием действий, необходимых для начала работы с хранилищем BLOB-объектов, очередями и таблицами.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Подключение к хранилищу Azure с помощью диалогового окна подключенных служб
1. Откройте проект в Visual Studio.

1. В **обозревателе решений** щелкните правой кнопкой мыши узел **Подключенные службы** и выберите в контекстном меню пункт **Добавить подключенную службу**.

    ![Добавление подключенной службы Azure](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. На странице **Подключенные службы** выберите элемент **Облачное хранилище в службе хранения Azure**.

    ![Добавление учетной записи хранения Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. В диалоговом окне **Служба хранилища Azure** выберите существующую учетную запись хранения и нажмите кнопку **Добавить**.

    Если вам нужно создать учетную запись хранения, перейдите к следующему шагу. В противном случае переходите к шагу 6.

    ![Добавление существующей учетной записи хранения в проект](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Чтобы создать учетную запись хранения, сделайте следующее:

   1. Щелкните **Создание новой учетной записи хранения** в нижней части диалогового окна.

   1. Заполните поля в диалоговом окне **Создание учетной записи хранения** и нажмите кнопку **Создать**.

       ![Новая учетная запись хранения Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Когда отобразится диалоговое окно **Служба хранилища Azure**, новая учетная запись хранения появится в списке. Выберите в списке новую учетную запись хранения и нажмите кнопку **Добавить**.

1. Подключенная служба хранилища появится в узле **Веб-ссылки** проекта.

## <a name="how-your-project-is-modified"></a>Какие изменения произойдут в проекте
Когда вы закроете диалоговое окно, Visual Studio добавит ссылки и внесет изменения в определенные файлы конфигурации. Конкретные изменения зависят от типа проекта.

- Проекты ASP.NET: ознакомьтесь со статьей [Приступая к работе с хранилищем BLOB-объектов Azure и подключенными службами Visual Studio (ASP.NET)](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs).
- Проекты ASP.NET Core: ознакомьтесь со статьей [Начало работы с хранилищем больших двоичных объектов Azure и подключенными службами Visual Studio (ASP.NET 5)](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs).
- Проекты облачной службы (веб-роли и рабочие роли): ознакомьтесь со статьей [Начало работы с хранилищем больших двоичных объектов Azure и подключенными службами Visual Studio (проектами облачных служб)](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs).
- Проекты веб-заданий: ознакомьтесь со статьей [Что произошло с моим проектом веб-заданий (подключенными к службе хранилища Azure службами Visual Studio)?](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Дальнейшие действия
- [Форум MSDN: хранилище Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Блог команды разработчиков службы хранилища Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Документация по службе хранилища Azure](/azure/storage/)
