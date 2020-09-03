---
title: Добавление Application Insights Azure с помощью Подключенные службы | Документация Майкрософт
description: Добавление Application Insights Azure в приложение с помощью Visual Studio для добавления подключенной службы
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643291"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Добавление Application Insights Azure с помощью Visual Studio Подключенные службы

С помощью Visual Studio вы можете подключить к Azure Application Insights любой из следующих компонентов, используя функцию **подключенные службы** :

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
## <a name="prerequisites"></a>Обязательные условия

- Visual Studio с установленной рабочей нагрузкой Azure.
- Проект одного из поддерживаемых типов

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Подключение к Azure Application Insights с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений**щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **Azure Application Insights**.

    ![Добавление Application Insights Azure](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/account/free).

1. На экране **настройка Application Insights Azure** выберите существующий компонент Application Insights Azure и нажмите кнопку **Далее**.

    Если необходимо создать новый компонент, перейдите к следующему шагу. В противном случае перейдите к шагу 7.

    ![Подключиться к существующему компоненту Application Insights](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Чтобы создать компонент Application Insights, выполните следующие действия.

   1. Выберите **создать новый Application Insights компонент** в нижней части экрана.

   1. Заполните **Application Insights: создать новый** экран и нажмите кнопку **создать**.

       ![Новый компонент Azure App Insights](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Когда откроется экран **настройка Application Insights Azure** , новый компонент появится в списке. Выберите новый компонент в списке и нажмите кнопку **Далее**.

1. Введите имя ключа инструментирования или выберите значение по умолчанию и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/azure-app-insights-add-connected-service/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Подключение появится в разделе " **зависимости службы** " на вкладке " **подключенные службы** ".

   ![Зависимости служб](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>См. также раздел

- [Страница продукта Azure Monitor](https://azure.microsoft.com/services/monitor/)
- [Документация по Azure App Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)
