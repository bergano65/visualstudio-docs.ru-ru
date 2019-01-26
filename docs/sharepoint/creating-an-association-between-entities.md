---
title: Создание ассоциации между сущностями | Документация Майкрософт
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
ms.openlocfilehash: bf5c914ba998c7690a20d4e1a573f8344f976061
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870731"
---
# <a name="create-an-association-between-entities"></a>Создание ассоциации между сущностями
  Можно определить отношения между сущностями в модели бизнес-данным (BDC) путем создания сопоставлений. Visual Studio создает методы, предоставляющие потребителям модели сведения о каждой ассоциации. Эти методы могут использоваться веб-частями SharePoint, списками или пользовательскими приложениями для отображения отношений данных в интерфейсе пользователя (ИП).  
  
## <a name="create-an-association"></a>Создание ассоциации
 Создайте ассоциацию, выбрав **ассоциации** управления в Visual Studio **элементов**, выбрав первую сущность (исходная сущность) и затем указав второй сущности (вызывается Целевая сущность). Можно указать сведения о связи в **Редактор ассоциаций**. Дополнительные сведения см. в разделе [Как Создание ассоциации между сущностями](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Методы связи
 Приложения, такие как веб-частей SharePoint business данных используют ассоциации, вызывая методы в классе службы сущности. Можно добавить методы в класс службы сущности, выбрав их в **Редактор ассоциаций**.  
  
 По умолчанию **Редактор ассоциаций** добавляет метод навигации ассоциаций в исходной и целевой сущности. Метод навигации ассоциаций в исходной сущности позволяет потребителям извлекать список сущностей назначения. Метод навигации ассоциаций в конечной сущности позволяет потребителям извлекать исходную сущность, которая связана с целевой сущностью.  
  
 Необходимо добавить код для каждого из этих методов, чтобы получать требуемые сведения. Можно также добавить другие типы методов для поддержки более сложных сценариев. Дополнительные сведения о каждом из этих методов, см. в разделе [поддерживаемые операции](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Типы ассоциаций
 В конструкторе BDC можно создать два типа сопоставлений: внешнего ассоциации на основе внешнего ключа и ассоциации.  
  
### <a name="foreign-key-based-association"></a>Связь с внешним на основе ключей
 Можно создать на основе ключей сопоставления на основе внешнего связать идентификатор в исходной сущности к типу дескрипторы, определенные в объект назначения. Это отношение позволяет потребителям модели обеспечивает пользовательский Интерфейс для своих пользователей. Например формы в Outlook, которая позволяет пользователю создавать заказа на продажу, в котором клиенты отображаются в раскрывающемся списке; или список заказов на продажу в SharePoint, позволяющий пользователям открыть страницу профиля для клиента.  
  
 Создание внешнего сопоставления на основе ключей, связать идентификаторы и дескрипторы типа, имеющие одно и то же имя и тип. Например, можно создать на основе ключей сопоставления на основе внешнего между `Contact` сущности и `SalesOrder` сущности. `SalesOrder` Возвращают `ContactID` дескриптор типа как часть возвращаемого параметра поиска и конкретного метода поиска. Оба дескриптора типа отображаются в **Редактор ассоциаций**. Чтобы создать на основе ключей связь по внешнему между `Contact` сущности и `SalesOrder` сущности, выберите `ContactID` идентификатор рядом с каждым из этих полей.  
  
 Добавьте код в метод навигации ассоциаций исходной сущности, возвращающий коллекцию сущностей назначения. В следующем примере возвращается заказов на продажу для контакта.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Добавьте код в метод навигации ассоциаций конечной сущности, который возвращает исходной сущности. В следующем примере возвращается контакта, который относится к заказу на продажу.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Ассоциацию без внешнего ключа
 Можно создать ассоциацию без сопоставления идентификаторов дескрипторам типа поля. Создайте этот вид связи, когда исходная сущность не имеет прямой связи с конечной сущности. Например `SalesOrderDetail` таблица не содержит внешний ключ, который сопоставляется с первичным ключом в `Contact` таблицы.  
  
 Если вы хотите отобразить информацию в `SalesOrderDetail` таблицы, к которому относится `Contact`, можно создать ассоциацию без внешнего ключа между `Contact` сущности и `SalesOrderDetail` сущности.  
  
 В методе навигации ассоциаций `Contact` сущности, возвращаемого `SalesOrderDetail` сущностей путем соединения таблиц, либо путем вызова хранимой процедуры.  
  
 Следующий пример возвращает сведения обо всех заказах путем соединения таблиц.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 В методе навигации ассоциаций `SalesOrderDetail` сущности, возвращать связанные `Contact`. В следующем примере это показано.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>См. также
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Практическое руководство. Создание ассоциации между сущностями](../sharepoint/how-to-create-an-association-between-entities.md)  
