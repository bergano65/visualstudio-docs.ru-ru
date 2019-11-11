---
title: Как добавить сущность в модель | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1a7ec1eab5cdcf2e415a4803c51c9da91be29c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985245"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Как добавить сущность в модель
  Чтобы создать сущность, добавьте элемент управления сущности из **панели элементов** Visual Studio в конструктор подключения к бизнес-данным (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Добавление сущности в модель

1. Создайте проект BDC или откройте существующий проект BDC. Дополнительные сведения см. [в статье Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

2. В **области элементов**в группе **бусинессдатакаталог** добавьте элемент управления **сущности** в конструктор.

     Новая сущность появится в конструкторе. Visual Studio добавляет элемент `<Entity>` в XML-файл модели BDC в проекте. Дополнительные сведения об атрибутах элемента сущности см. в разделе [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. В конструкторе откройте контекстное меню сущности, выберите **Добавить**, а затем выберите **идентификатор**.

     В сущности появится новый идентификатор.

    > [!NOTE]
    > Имя сущности и идентификатор можно изменить в окне **Свойства** .

4. Определите поля сущности в классе. Можно либо добавить новый класс в проект, либо использовать существующий класс, созданный с помощью других средств, таких как реляционный конструктор объектов (реляционный конструктор R). В следующем примере показан класс сущностей с именем Contact.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>См. также
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
