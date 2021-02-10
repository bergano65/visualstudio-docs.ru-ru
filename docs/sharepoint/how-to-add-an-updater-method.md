---
title: Как добавить метод обновления | Документация Майкрософт
description: Узнайте, как разрешить пользователям обновлять бизнес-данные в внешнем списке SharePoint, добавив метод обновления.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fff7083305d4e19495b81525c8a67a42c5ff6c70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967505"
---
# <a name="how-to-add-an-updater-method"></a>Как добавить метод обновления
  Вы можете разрешить пользователям обновлять бизнес-данные в внешнем списке SharePoint, создав метод *обновления* . Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Создание метода обновления

1. В конструкторе BDC выберите сущность.

2. В строке меню выберите **Просмотреть**  >  **другие**  >  **сведения о методе BDC** Windows.

    Откроется окно сведения о методе BDC. Дополнительные сведения об этом окне см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод обновления**.

    Visual Studio добавляет в модель следующие элементы. Эти элементы отображаются в окне сведения о методе BDC.

   - Метод с именем **Update**.

   - Входной параметр для метода.

   - Дескриптор типа для параметра. По умолчанию Visual Studio использует дескриптор типа сущности, определенный для метода Finder (например: Contact).

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Если идентификатор типа сущности представляет поле в таблице базы данных, которое не создается автоматически, установите для свойства **поля перед обновлением** **значение true**.

4. В **Обозреватель решений** откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**.

    Файл кода службы сущности откроется в **редакторе кода**. Дополнительные сведения об этом файле см. [в разделе Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод Update для обновления данных. В следующем примере информация для контакта обновляется в образце базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>См. также раздел
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
