---
title: Как добавить сущность в модель | Документация Майкрософт
description: Добавьте сущность в модель, добавив элемент управления сущность из панели элементов Visual Studio в конструктор подключения к бизнес-данным (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1d900639463f727a23c4fafab6f077f787c5ca04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959978"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Как добавить сущность в модель
  Чтобы создать сущность, добавьте элемент управления сущности из **панели элементов** Visual Studio в конструктор подключения к бизнес-данным (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Добавление сущности в модель

1. Создайте проект BDC или откройте существующий проект BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

2. В **области элементов** в группе **бусинессдатакаталог** добавьте элемент управления **сущности** в конструктор.

     Новая сущность появится в конструкторе. Visual Studio добавляет `<Entity>` элемент в XML-файл модели BDC в проекте. Дополнительные сведения об атрибутах элемента сущности см. в разделе [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. В конструкторе откройте контекстное меню сущности, выберите **Добавить**, а затем выберите **идентификатор**.

     В сущности появится новый идентификатор.

    > [!NOTE]
    > Имя сущности и идентификатор можно изменить в окне **Свойства** .

4. Определите поля сущности в классе. Можно либо добавить новый класс в проект, либо использовать существующий класс, созданный с помощью других средств, таких как реляционный конструктор объектов (реляционный конструктор R). В следующем примере показан класс сущностей с именем Contact.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>См. также раздел
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
