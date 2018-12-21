---
title: Управление ресурсами Azure с помощью Cloud Explorer | Документация Майкрософт
description: Узнайте, как использовать Cloud Explorer для просмотра и управления ресурсами Azure в Visual Studio.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: a5b75aa5e1310e02befe162199472eef987d7cd9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002364"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Управление ресурсами, связанными с учетными записями Azure, в Visual Studio Cloud Explorer

Cloud Explorer позволяет просматривать ресурсы Azure и групп ресурсов, проверять их свойства и выполнять основные диагностические действия разработчика из среды Visual Studio. 

Как и [портала Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer построено на стеке Azure Resource Manager. Таким образом, Cloud Explorer распознает ресурсы, такие как группы ресурсов Azure и служб Azure, таких как приложения логики и приложения API, а также поддерживает [управление доступом на основе ролей](/azure/role-based-access-control/role-assignments-portal.md) (RBAC). 

## <a name="prerequisites"></a>Предварительные требования

* Visual Studio 2015 с [Microsoft Azure SDK для .NET 2.9](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Учетная запись Microsoft Azure — Если у вас нет учетной записи, вы можете [зарегистрироваться для получения бесплатной пробной версии](http://go.microsoft.com/fwlink/?LinkId=623901) или [активируйте преимущества для подписчиков Visual Studio](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Чтобы открыть Cloud Explorer, выберите **представление** > **Cloud Explorer** в строке меню.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Добавьте Azure учетной записи в Cloud Explorer

Чтобы просмотреть ресурсы, связанные с учетной записью Azure, необходимо сначала добавить учетную запись в Cloud Explorer. 

1. В **Cloud Explorer**выберите **параметры учетной записи Azure**.

   ![Значок параметров учетной записи Azure в обозревателе облака](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Выберите **управление учетными записями**. 

   ![Ссылка Добавление учетной записи Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Войдите в учетную запись Azure, ресурсы которого нужно просмотреть. 

1. После входа в учетную запись Azure, отображения подписок, связанных с этой учетной записи. Установите флажки для тех подписок учетной записи, вы хотите просмотреть, а затем выберите **применить**. 

   ![Cloud Explorer: Выбор подписок Azure для отображения](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. После выбора подписки, ресурсы которого нужно просмотреть, эти подписки отобразятся все ресурсы в Cloud Explorer.

   ![Cloud Explorer список ресурсов для учетной записи Azure](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Удаление учетной записи Azure из Cloud Explorer 

1. В **Cloud Explorer**выберите **управление учетными записями**.

   ![Значок параметров учетной записи Azure в обозревателе облака](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Рядом с учетной записи, которую необходимо удалить, выберите **управление учетными записями**.

   ![Значок параметров учетной записи Azure в обозревателе облака](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Выберите **удалить** удалить учетную запись.

    ![Cloud Explorer управление учетные записи диалоговое окно](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Просмотр типов ресурсов или групп ресурсов

Для просмотра ресурсов Azure, вы можете **типов ресурсов** или **групп ресурсов** представления.

1. В **Cloud Explorer**, выберите раскрывающийся список представления ресурсов.

   ![Раскрывающийся список Cloud Explorer выберите нужное представление ресурсов](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. В контекстном меню выберите нужное представление: 

   * **Типы ресурсов** представление - общее представление, используемые на [портала Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040), отображает ресурсы Azure с упорядочением по типам, например веб-приложений, учетные записи хранения и виртуальные машины. 
   * **Группы ресурсов** представление - упорядочивает ресурсы Azure по группам ресурсов Azure, с которым они связаны. Группа ресурсов представляет собой набор ресурсов Azure, обычно используется в конкретном приложении. Дополнительные сведения о группах ресурсов Azure, см. в разделе [Обзор диспетчера ресурсов Azure](/azure/azure-resource-manager/resource-group-overview).

   На следующем рисунке показана сравнение оба представления ресурсов:

   ![Сравнение представлений ресурсов обозреватель облака](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Просмотр и поиск ресурсов в Cloud Explorer

Для перехода к ресурсу Azure и просмотра его информации в Cloud Explorer разверните элемента типа ресурса или группу, а затем выберите ресурс. При выборе ресурса, сведения отображаются на двух вкладках - **действия** и **свойства** — в нижней части Cloud Explorer.

* **Действия** вкладке - перечислены действия, которые можно выполнять в Cloud Explorer для выбранного ресурса. Эти параметры можно также просмотреть, щелкнув правой кнопкой мыши ресурс, чтобы просмотреть ее контекстное меню.

* **Свойства** вкладке - показывает свойства ресурса, например его тип, языковой стандарт и группа ресурсов с которым он связан.

Ниже сравнения представлены сведения, отображаемые на каждой вкладке для службы приложений:

  ![Снимок экрана: Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Каждый ресурс имеет действие **открыть на портале**. При выборе этого действия приложение Cloud Explorer отобразит выбранный ресурс [портала Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). **Открыть на портале** функция удобна для перехода к ресурсам с глубоким.

Дополнительные действия и значения свойств могут также отображаться с учетом ресурсов Azure. Например, веб-приложений и logic apps также иметь действия **открыть в браузере** и **подключить отладчик** в дополнение к **открыть на портале**. Действия их открытия в редакторах отображаются при выборе учетной записи хранилища BLOB-объектов, очередей или таблиц. Приложения, Azure, имеют **URL-адрес** и **состояние** свойства, тогда как свойства строки ключа и подключения ресурсов хранилища.

## <a name="find-resources-in-cloud-explorer"></a>Поиск ресурсов в Cloud Explorer

Чтобы найти ресурсы с определенным именем в подписках учетной записи Azure, введите имя в **поиска** в Cloud Explorer.

  ![Поиск ресурсов в Cloud Explorer](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

При вводе символов в **поиска** , только те ресурсы, которые соответствуют этим символам отображаться в дереве ресурсов остаются.
