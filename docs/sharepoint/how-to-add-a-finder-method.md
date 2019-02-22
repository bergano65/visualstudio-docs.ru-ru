---
title: Практическое руководство. Добавление метода Finder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: dc61db134063c1e300a2620f611d62497fffe6e1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608075"
---
# <a name="how-to-add-a-finder-method"></a>Практическое руководство. Добавление метода Finder
  Чтобы включить службу бизнес-данным (BDC) для отображения списка сущностей в веб-части или списке, необходимо создать *Finder* метод. Метод поиска — это специальный метод, который возвращает коллекцию экземпляров сущности. Дополнительные сведения см. в разделе [проектирование Business Data Connectivity Model](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Чтобы создать метод поиска

1. На **конструкторе BDC**, выберите сущность.

    Дополнительные сведения см. в разделе [Как Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. В строке меню выберите **представление** > **Other Windows** > **Подробности метода BDC**.

    **Подробности метода BDC** откроется окно. Дополнительные сведения о **Подробности метода BDC** окно, см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В **добавьте метод** выберите **создать метод поиска**.

    Visual Studio добавляет метод, возвращаемый параметр и дескриптор типа.

4. Настройте дескриптор типа как дескриптор типа коллекции сущностей. Дополнительные сведения о создании дескриптора типа коллекции сущностей см. в разделе [как: Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   >  Необходимо выполнить этот шаг, если вы добавили конкретного метода поиска для сущности. Visual Studio использует дескриптор типа, определенного в конкретный метод поиска.

5. В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и затем выберите **Просмотр кода**. Дополнительные сведения о файле кода службы, см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Добавьте код в метод Finder. Этот код выполняет следующие задачи:

   - Извлекает данные из источника данных.

   - Возвращает список сущностей в службу BDC.

     В следующем примере возвращается коллекция `Contact` сущностями с помощью данных из образца базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   >  Замените значение `ServerName` поле с именем сервера.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>См. также
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
