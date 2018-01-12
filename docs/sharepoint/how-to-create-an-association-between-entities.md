---
title: "Как: Создание ассоциации между сущностями | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AssociationGroupTool
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49b4d68a8d957462954c998d96e9309944cdb9f5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-association-between-entities"></a>Практическое руководство. Создание ассоциации между сущностями
  Можно определить отношения между сущностями в модели бизнес-данным (BDC) путем создания связи. Visual Studio создает методы, предоставляющие потребителям модели сведения о каждой ассоциации. Эти методы могут использоваться веб-частями SharePoint, списками или пользовательскими приложениями для отображения отношений данных в интерфейсе пользователя (ИП).  
  
 В конструкторе BDC можно создать два типа ассоциаций: внешний ассоциации на основе внешнего ключа и ассоциации. Дополнительные сведения см. в разделе [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Для создания ассоциации между сущностями  
  
1.  На **BusinessDataConnectivity** вкладке **элементов**, выберите **ассоциации** элемента.  
  
2.  В конструкторе BDC последовательно выберите исходную и конечную сущности.  
  
     **Редактор ассоциаций** отображается.  
  
3.  Если вы хотите создать ассоциацию внешнего на основе ключей, выберите **связь с внешним ключом** флажок.  
  
    1.  В **идентификатор источника** столбец **сопоставление идентификатора** таблицы, выберите идентификатор рядом с каждым соответствующим дескриптором типа, который отображается в **поле** столбца.  
  
         Например, в **идентификатор источника** выберите `ContactID` рядом с `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` дескриптор типа и `ReadItem.salesOrder.SalesOrder.ContactID` дескриптор типа.  
  
4.  Если вы хотите создать ассоциацию без внешнего ключа, снимите **связь с внешним ключом** флажок.  
  
5.  Нажмите кнопку **ОК** .  
  
6.  В конструкторе BDC появится строка, представляющий взаимосвязь между исходной и конечной сущности.  
  
     Visual Studio добавляет метод навигации ассоциаций конечной сущности класс службы и класс службы исходной сущности. Дополнительные сведения о методах навигации см. в разделе [поддерживаемые операции](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  В методе навигации ассоциаций исходной сущности добавьте код, возвращающий коллекцию конечных сущностей.  
  
8.  В методе навигации ассоциаций конечной сущности добавьте код, который возвращает связанные исходной сущности.  
  
     Примеры методов навигации ассоциаций см. в разделе [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>См. также  
 [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Как: определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)   
 [Как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Пошаговое руководство. Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  