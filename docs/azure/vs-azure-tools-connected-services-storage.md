---
title: Добавление службы хранилища Azure с помощью подключенных служб | Документация Майкрософт
description: Добавление в приложение зависимости службы хранилища Azure с помощью Visual Studio Подключенные службы
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: f2f55a149420205435d9f64ea1f66c8c6854ec38
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800519"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Добавление хранилища Azure с использованием подключенных служб Visual Studio

С помощью Visual Studio вы можете подключить к службе хранилища Azure любой из следующих компонентов, используя функцию **подключенные службы** :

- .NET Framework консольное приложение
- ASP.NET MVC (.NET Framework)
- ASP.NET Core
- .NET Core (включая консольное приложение, WPF, Windows Forms, библиотеку классов)
- Рабочая роль .NET Core
- Функции Azure
- Приложение универсальная платформа Windows
- Xamarin
- Cordova

Подключенные службы добавляют необходимые ссылки и код подключения в проект и вносят соответствующие изменения в файлы конфигурации.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Подключенные службы в Visual Studio для Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Предварительные требования

- Visual Studio с установленной рабочей нагрузкой Azure.
- Проект одного из поддерживаемых типов

## <a name="connect-to-azure-storage-using-connected-services"></a>Подключение к службе хранилища Azure с помощью Подключенные службы

::: moniker range="vs-2017"

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений**щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

    ![Добавление подключенной службы Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

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
:::moniker-end

:::moniker range=">=vs-2019"

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений**щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

    ![Добавление подключенной службы Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **хранилище Azure**.

    ![Добавление учетной записи хранения Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/account/free).

1. На экране **Настройка службы хранилища Azure** выберите существующую учетную запись хранения и нажмите кнопку **Далее**.

    Если вам нужно создать учетную запись хранения, перейдите к следующему шагу. В противном случае переходите к шагу 6.

    ![Добавление существующей учетной записи хранения в проект](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Чтобы создать учетную запись хранения, сделайте следующее:

   1. Выберите **создать учетную запись хранения** в нижней части диалогового окна.

   1. Заполните службу **хранилища Azure: Создайте** диалоговое окно и нажмите кнопку **создать**.

       ![Новая учетная запись хранения Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Когда отобразится диалоговое окно **Служба хранилища Azure**, новая учетная запись хранения появится в списке. Выберите новую учетную запись хранения в списке и нажмите кнопку **Далее**.

1. Введите имя строки подключения и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Подключенная служба хранилища появится в узле **Веб-ссылки** проекта.
:::moniker-end

## <a name="see-also"></a>См. также раздел

- [Форум службы хранилища Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Документация по службе хранилища Azure](/azure/storage/)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)
