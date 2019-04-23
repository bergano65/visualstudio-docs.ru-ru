---
title: Практическое руководство. Создание ассоциации между сущностями | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce6d0bad9da4f11b5fae1daf93657c6908cf5e95
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092569"
---
# <a name="how-to-create-an-association-between-entities"></a>Практическое руководство. Создание ассоциации между сущностями
  Можно определить отношения между сущностями в модели бизнес-данным (BDC) путем создания сопоставлений. Visual Studio создает методы, предоставляющие потребителям модели сведения о каждой ассоциации. Эти методы могут использоваться веб-частями SharePoint, списками или пользовательскими приложениями для отображения отношений данных в интерфейсе пользователя (ИП).

 В конструкторе BDC можно создать два типа сопоставлений: внешнего ассоциации на основе внешнего ключа и ассоциации. Дополнительные сведения см. в разделе [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Для создания ассоциации между сущностями

1. На **BusinessDataConnectivity** вкладке **элементов**, выберите **ассоциации** элемента.

2. В конструкторе BDC последовательно выберите исходную и конечную сущности.

     **Редактор ассоциаций** отображается.

3. Если вы хотите создать ассоциацию внешнего на основе ключей, выберите **связь с внешним ключом** "флажок".

    1. В **идентификатор источника** столбец **сопоставление идентификатора** выберите идентификатор рядом с каждым соответствующим дескриптором типа, которое отображается в **поле** столбца.

         Например, в **идентификатор источника** столбец, выберите `ContactID` рядом с полем `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` дескриптора типа и `ReadItem.salesOrder.SalesOrder.ContactID` дескриптор типа.

4. Если вы хотите создать ассоциацию без внешнего ключа, снимите **связь с внешним ключом** "флажок".

5. Нажмите кнопку **ОК** .

6. В конструкторе BDC появится строка, представляющий взаимосвязь между исходной и целевой сущностями.

     Visual Studio добавляет метод навигации ассоциаций к классу службы конечной сущности и класс службы исходной сущности. Дополнительные сведения о методах навигации ассоциаций см. в разделе [поддерживаемые операции](http://go.microsoft.com/fwlink/?LinkId=169286).

7. В методе навигации ассоциаций исходной сущности добавьте код, возвращающий коллекцию сущностей назначения.

8. В методе навигации ассоциаций конечной сущности добавьте код, который возвращает связанные исходной сущности.

     Примеры методов навигации ассоциаций см. в разделе [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>См. также
- [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
- [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Пошаговое руководство: Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
