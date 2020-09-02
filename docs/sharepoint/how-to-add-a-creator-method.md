---
title: Как добавить метод Creator | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 962e353b5ae82f6dd3eccc2898385fd4b9ee30ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017064"
---
# <a name="how-to-add-a-creator-method"></a>Как добавить метод Creator
  Метод Creator добавляет новые данные в источник данных сущности. Служба подключения к бизнес-данным (BDC) вызывает этот метод, когда пользователь наберет кнопку **создать элемент** на **ленте** списка, основанного на модели. Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Добавление метода Creator

1. В **конструкторе BDC**выберите сущность.

2. В строке меню выберите **Просмотреть**  >  **другие**  > **сведения о методе BDC**Windows.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения об этом окне см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод создания**.

    Visual Studio добавляет в модель следующие элементы, и эти элементы отображаются в окне **сведения о методе BDC** .

   - Метод с именем **CREATE**.

   - Входной параметр для метода.

   - Возвращаемый параметр для метода.

   - Дескрипторы типов для параметров.

   - Экземпляр метода для метода.

     Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. В **Обозреватель решений**откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**.

    Файл кода службы сущности откроется в редакторе кода. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод Creator, который добавляет данные в источник данных. В следующем примере к образцу базы данных AdventureWorks добавляется контакт для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>См. также раздел
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
