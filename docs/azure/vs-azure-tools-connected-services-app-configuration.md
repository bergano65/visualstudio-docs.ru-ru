---
title: Добавление конфигурации приложения Azure с помощью Подключенные службы | Документация Майкрософт
description: Добавление в приложение зависимости службы настройки Azure с помощью Visual Studio Подключенные службы
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727298"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Добавление конфигурации приложения Azure с помощью Visual Studio Подключенные службы

В этом руководстве вы узнаете, как легко добавить все необходимое для начала использования конфигурации приложений Azure, чтобы управлять параметрами конфигурации и флагами для веб-проектов в Visual Studio, независимо от того, используется ASP.NET Core или любой тип проекта ASP.NET. С помощью функции Подключенные службы в Visual Studio можно автоматически добавить в Visual Studio весь код, пакеты NuGet и параметры конфигурации, необходимые для подключения к ресурсу конфигурации приложения в Azure. Чтобы использовать эту функцию, необходимо использовать Visual Studio 2019 версии 16,9 или более поздней.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Подключенные службы в Visual Studio для Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Предварительные требования

- Visual Studio с установленной рабочей нагрузкой Azure.
- Проект одного из поддерживаемых типов

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Подключение к конфигурации приложения Azure с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений** щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

    ![Добавление подключенной службы Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **Конфигурация приложения Azure**.

    ![Добавление конфигурации приложения](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/free/dotnet).

1. На экране **Настройка конфигурации приложения Azure** выберите подписку и существующее хранилище конфигураций. Нажмите кнопку **Далее**.

    Если необходимо создать хранилище конфигураций приложений, перейдите к следующему шагу. В противном случае переходите к шагу 6.

    ![Добавить существующую учетную запись конфигурации в проект](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Чтобы создать хранилище конфигурации приложения, выполните следующие действия.

   1. Щелкните значок + справа от заголовка **хранилища конфигурации приложений** . 

   1. Заполните **конфигурацию приложения Azure: создать** диалоговое окно и нажмите кнопку **создать**. Обратите внимание, что поле имя ресурса должно быть уникальным. 

       ![Новое хранилище конфигураций приложений Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Когда откроется диалоговое окно **настройки приложения Azure** , в списке появится новое хранилище конфигураций. Выберите это новое хранилище, а затем нажмите кнопку **Далее**.

1. Введите имя строки подключения и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. После завершения **процесса настройки зависимостей** в узле " **зависимости службы** " проекта будет отображаться Конфигурация приложения Azure.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о конфигурации приложений Azure см. в [документации по конфигурации приложений Azure](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>См. также раздел

- [Руководство по использованию динамической конфигурации в конфигурации приложения, подключенной ASP.NET Core приложении](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)