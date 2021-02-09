---
title: Как создать ассоциацию между сущностями | Документация Майкрософт
description: Определение связей между сущностями в модели подключения к бизнес-данным (BDC) путем создания ассоциаций в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e726e8b5702a656b340401c9a2db26e40be1a37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925569"
---
# <a name="how-to-create-an-association-between-entities"></a>Как создать ассоциацию между сущностями
  Отношения между сущностями в модели подключения к бизнес-данным (BDC) можно определить путем создания ассоциаций. Visual Studio создает методы, предоставляющие потребителям модели сведения о каждой ассоциации. Эти методы могут использоваться веб-частями SharePoint, списками или пользовательскими приложениями для отображения отношений данных в интерфейсе пользователя (ИП).

 В конструкторе BDC можно создать два типа ассоциаций: связи на основе внешних ключей и ассоциации без внешнего ключа. Дополнительные сведения см. в разделе [Создание связи между сущностями](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Создание связи между сущностями

1. На вкладке **BusinessDataConnectivity** на **панели элементов** выберите элемент **Ассоциация** .

2. В конструкторе BDC последовательно выберите исходную и конечную сущности.

     Откроется **Редактор взаимосвязей** .

3. Если вы хотите создать ассоциацию на основе внешнего ключа, установите флажок **является связью с внешним ключом** .

    1. В столбце **идентификатор источника** таблицы **сопоставление идентификаторов** выберите идентификатор рядом с каждым соответствующим дескриптором типа, который отображается в столбце **поле** .

         Например, в столбце **идентификатор источника** выберите `ContactID` рядом с `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` дескриптором типа и `ReadItem.salesOrder.SalesOrder.ContactID` дескриптором типа.

4. Если вы хотите создать ассоциацию без внешнего ключа, снимите флажок **связь с внешним ключом** .

5. Нажмите кнопку **ОК** .

6. В конструкторе BDC отображается строка, представляющая ассоциацию между исходной сущностью и целевой сущностью.

     Visual Studio добавляет метод навигатора ассоциаций в класс службы целевой сущности и класс службы исходной сущности. Дополнительные сведения о методах навигации ассоциаций см. в разделе [Поддерживаемые операции](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. В методе навигатора ассоциаций исходной сущности добавьте код, возвращающий коллекцию целевых сущностей.

8. В методе навигатора ассоциаций целевой сущности добавьте код, который возвращает связанную исходную сущность.

     Примеры методов навигатора ассоциаций см. в разделе [Создание связи между сущностями](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>См. также раздел
- [Создание связи между сущностями](../sharepoint/creating-an-association-between-entities.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Пошаговое руководство. Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
