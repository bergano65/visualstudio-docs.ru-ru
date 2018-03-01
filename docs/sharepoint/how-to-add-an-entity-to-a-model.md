---
title: "Как: Добавление сущности в модель | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 2ef3885f2a290fd1d4193daf9436a08ae5588a0d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-an-entity-to-a-model"></a>Практическое руководство. Добавление сущности в модель
  Чтобы создать сущность, добавление элемента управления сущности из Visual Studio **элементов** в конструктор бизнес-данным (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Чтобы добавить сущность в модель  
  
1.  Создайте или откройте существующий проект BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  В **элементов**, из **каталог бизнес-данных** группу, добавить **сущности** элемента управления в конструктор.  
  
     В конструкторе откроется новая сущность. Visual Studio добавляет `<Entity>` элемент в XML-файле модели в проекте. Дополнительные сведения об атрибутах элемента сущности см. в разделе [сущности](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  В конструкторе откройте контекстное меню для сущности, выберите **добавить**, а затем выберите **идентификатор**.  
  
     В сущности отобразится новый идентификатор.  
  
    > [!NOTE]  
    >  Можно изменить имя сущности и идентификатора в **свойства** окна.  
  
4.  Определите поля сущности в классе. Можно добавить новый класс в проект или использовать существующий класс, созданный с помощью других средств, таких как реляционный конструктор объектов (O/R-конструктор). В примере показан класс сущностей с именем Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  