---
title: Добавление кэша Azure для Redis с помощью Подключенные службы | Документация Майкрософт
description: Добавление в приложение кэша Azure для поддержки Redis с помощью Visual Studio для добавления подключенной службы
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 48554484781cca46ba96f8a075d18ea55ec3ef43
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398622"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Добавление кэша Azure для Redis с помощью Visual Studio Подключенные службы

С помощью Visual Studio вы можете подключить любой из следующих компонентов к кэшу Azure для Redis, используя функцию **подключенные службы** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Подключение к кэшу Azure для Redis с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений** щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **кэш Azure для Redis**.

    ![Добавление Кэша Azure для Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/account/free).

1. На экране **Настройка кэша Azure для Redis** выберите существующий кэш Azure для Redis и нажмите кнопку **Далее**.

    Если необходимо создать новый компонент, перейдите к следующему шагу. В противном случае перейдите к шагу 7.

    ![Подключение к существующему кэшу Azure для Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Чтобы создать кэш Redis для Azure, выполните следующие действия.

   1. Выберите **создать новый кэш Redis для Azure** в нижней части экрана.

   1. Заполните **кэш Azure для Redis: создать новый** экран и нажмите кнопку **создать**.

       ![Новый кэш Azure для Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Когда появится экран **Настройка кэша Azure для Redis** , в списке появится новый кэш. Выберите новую базу данных в списке и нажмите кнопку **Далее**.

1. Введите имя строки подключения или выберите значение по умолчанию и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Подключение появится в разделе " **зависимости службы** " на вкладке " **подключенные службы** ".

   ![Зависимости служб](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>См. также

- [Страница "кэш Azure для Redis продукта"](https://azure.microsoft.com/services/cache)
- [Документация по кэшу Azure для Redis](/azure/azure-cache-for-redis/)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)