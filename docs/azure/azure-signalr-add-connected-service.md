---
title: Добавление Azure SignalR с помощью Подключенные службы | Документация Майкрософт
description: Добавление в приложение Azure SignalR с помощью Visual Studio для добавления подключенной службы
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0e44416bd6a55796b62a7590856caab8466a6401
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643252"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Добавление Azure SignalR с помощью Visual Studio Подключенные службы

С помощью Visual Studio вы можете подключить к службе Azure SignalR любой из следующих компонентов, используя функцию **подключенные службы** :

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Подключение к SignalR Azure с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений**щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **служба Azure SignalR**.

    ![Добавление службы Azure SignalR](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/account/free).

1. На экране **Настройка Azure SignalR** выберите существующий компонент Azure SignalR и нажмите кнопку **Далее**.

    Если необходимо создать новый компонент, перейдите к следующему шагу. В противном случае перейдите к шагу 7.

    ![Подключение к существующему компоненту SignalR Azure](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Чтобы создать экземпляр службы Azure SignalR, выполните следующие действия.

   1. В нижней части экрана выберите **создать новый экземпляр службы Azure SignalR** .

   1. Заполните **службу Azure SignalR: создать новый** экран и нажмите кнопку **создать**.

       ![Новый экземпляр службы Azure SignalR](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Когда откроется экран **Настройка службы SignalR Azure** , в списке появится новый экземпляр. Выберите новый экземпляр в списке и нажмите кнопку **Далее**.

1. Введите имя строки подключения или выберите значение по умолчанию и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/azure-signalr-add-connected-service/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Подключение появится в разделе " **зависимости службы** " на вкладке " **подключенные службы** ".

   ![Зависимости служб](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>См. также

- [Страница продукта Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Документация по Службе Azure SignalR](/azure/azure-signalr)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)
