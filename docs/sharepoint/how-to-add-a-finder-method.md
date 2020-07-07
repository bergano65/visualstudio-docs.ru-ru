---
title: Как добавить метод Finder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fa8f8eb34943cc17bc6cabca8e93ea7569a7ba6
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016733"
---
# <a name="how-to-add-a-finder-method"></a>Как добавить метод Finder
  Чтобы служба подключения к бизнес-данным (BDC) отображала список сущностей в веб-части или списке, необходимо создать метод *поиска* . Метод поиска — это специальный метод, который возвращает коллекцию экземпляров сущности. Дополнительные сведения см. [в разделе Разработка модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Создание метода Finder

1. В **конструкторе BDC**выберите сущность.

    Дополнительные сведения см. [в разделе инструкции. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. В строке меню выберите **Просмотреть**  >  **другие**  >  **сведения о методе BDC**Windows.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения о окне **сведения о методе BDC** см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод поиска**.

    Visual Studio добавляет метод, возвращаемый параметр и дескриптор типа.

4. Настройте дескриптор типа в качестве дескриптора типа коллекции сущностей. Дополнительные сведения о создании дескриптора типа коллекции сущностей см. в разделе [инструкции. определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Вам не нужно выполнять этот шаг, если вы добавили в сущность конкретный метод поиска. Visual Studio использует дескриптор типа, определенный в конкретном методе поиска.

5. В **Обозреватель решений**откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**. Дополнительные сведения о файле кода службы см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Добавьте код в метод Finder. Этот код выполняет следующие задачи:

   - Извлекает данные из источника данных.

   - Возвращает список сущностей для службы BDC.

     В следующем примере возвращается коллекция `Contact` сущностей с использованием данных из образца базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>См. также раздел
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
