---
title: Создание связи между сущностями | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: ee767ded0687baa09653bd82785b68bee7fa0ebd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981093"
---
# <a name="create-an-association-between-entities"></a>Создание связи между сущностями
  Отношения между сущностями в модели подключения к бизнес-данным (BDC) можно определить путем создания ассоциаций. Visual Studio создает методы, предоставляющие потребителям модели сведения о каждой ассоциации. Эти методы могут использоваться веб-частями SharePoint, списками или пользовательскими приложениями для отображения отношений данных в интерфейсе пользователя (ИП).

## <a name="create-an-association"></a>Создание связи
 Создайте связь, выбрав элемент управления **взаимосвязь** на **панели элементов**Visual Studio, выбрав первую сущность (называемую исходной сущностью), а затем выбрав вторую сущность (называемую целевой сущностью). Сведения о сопоставлении можно определить в **редакторе взаимосвязей**. Дополнительные сведения см. [в разделе инструкции. Создание связи между сущностями](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Методы взаимосвязей
 Такие приложения, как веб-части бизнес-данных SharePoint используют ассоциации, вызывая методы в классе службы сущности. Можно добавить методы в класс службы сущности, выбрав их в **редакторе взаимосвязей**.

 По умолчанию **Редактор взаимосвязей** добавляет метод навигации ассоциаций в исходную и целевую сущности. Метод навигации ассоциаций в исходной сущности позволяет пользователям получить список целевых сущностей. Метод навигации взаимосвязей в целевой сущности позволяет потребителям извлекать исходную сущность, связанную с целевой сущностью.

 Необходимо добавить код в каждый из этих методов, чтобы получить соответствующие сведения. Можно также добавить другие типы методов для поддержки более сложных сценариев. Дополнительные сведения о каждом из этих методов см. в разделе [Поддерживаемые операции](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Типы ассоциаций
 В конструкторе BDC можно создать два типа ассоциаций: связи на основе внешних ключей и ассоциации без внешнего ключа.

### <a name="foreign-key-based-association"></a>Ассоциация на основе внешнего ключа
 Можно создать ассоциацию на основе внешнего ключа, соотнесенную идентификатор в исходной сущности с дескрипторами типа, определенными в целевой сущности. Эта связь позволяет потребителям модели предоставлять расширенный пользовательский интерфейс для своих пользователей. Например, форма в Outlook, позволяющая пользователю создать заказ на продажу, который может отображать клиентов в раскрывающемся списке; или список заказов на продажу в SharePoint, который позволяет пользователям открывать страницу профиля для клиента.

 Чтобы создать ассоциацию на основе внешнего ключа, свяжите идентификаторы и дескрипторы типов, имеющие одинаковое имя и тип. Например, вы можете создать ассоциацию на основе внешнего ключа между сущностью `Contact` и сущностью `SalesOrder`. Сущность `SalesOrder` возвращает дескриптор типа `ContactID` как часть возвращаемого параметра метода поиска или конкретных методов поиска. Оба дескриптора типа отображаются в **редакторе взаимосвязей**. Чтобы создать связь на основе внешнего ключа между сущностью `Contact` и `SalesOrder` сущностью, выберите идентификатор `ContactID` рядом с каждым из этих полей.

 Добавьте код в метод навигатора ассоциаций исходной сущности, которая возвращает коллекцию целевых сущностей. В следующем примере возвращаются заказы на продажу для контакта.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Добавьте код в метод навигатора ассоциаций целевой сущности, который возвращает исходную сущность. В следующем примере возвращается контакт, связанный с заказом на продажу.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Ассоциация без внешнего соединения
 Можно создать ассоциацию без сопоставления идентификаторов с дескрипторами типов полей. Создать связь такого типа, когда исходная сущность не имеет прямой связи с целевой сущностью. Например, `SalesOrderDetail`ная таблица не содержит внешнего ключа, который сопоставляется с первичным ключом в `Contact` таблице.

 Если необходимо отобразить сведения в таблице `SalesOrderDetail`, связанной с `Contact`, можно создать ассоциацию без внешнего соединения между сущностью `Contact` и `SalesOrderDetail` сущностью.

 В методе навигации ассоциации сущности `Contact` сущность возвращает `SalesOrderDetail` сущности путем соединения таблиц или путем вызова хранимой процедуры.

 В следующем примере возвращаются сведения обо всех заказах на продажу путем соединения таблиц.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 В методе навигации ассоциацию `SalesOrderDetail` сущности верните связанный `Contact`. В следующем примере это показано.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>См. также
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как создать ассоциацию между сущностями](../sharepoint/how-to-create-an-association-between-entities.md)
