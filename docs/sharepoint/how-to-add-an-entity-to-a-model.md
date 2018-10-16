---
title: 'Практическое: Добавление сущности в модель | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 72dbebd8ff9b2e7bf7b001d540158656271c0556
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757724"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Практическое: Добавление сущности в модель
  Чтобы создать сущность, добавьте элемент управления сущности из Visual Studio **элементов** в конструктор бизнес-данным (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Чтобы добавить сущность в модель  
  
1.  Создание проекта BDC, или откройте существующий проект BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  В **элементов**, из **каталог бизнес-данных** группу, добавить **сущности** элемента управления в конструктор.  
  
     В конструкторе отобразится новая сущность. Visual Studio добавляет `<Entity>` элемент к XML-файла модели BDC в проекте. Дополнительные сведения об атрибутах элемента сущности, см. в разделе [сущности](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  В конструкторе, откройте контекстное меню для сущности, выберите **добавить**, а затем выберите **идентификатор**.  
  
     Отобразится новый идентификатор для сущности.  
  
    > [!NOTE]  
    >  Можно изменить имя сущности и идентификатора в **свойства** окна.  
  
4.  Определение полей сущности в классе. Можно добавить новый класс в проект или использовать существующий класс, созданный с помощью других средств, таких как реляционный конструктор объектов (O/R Designer). Следующий пример показывает класс сущностей с именем контакта.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>См. также
 [Практическое: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Практическое: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Практическое: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Практическое: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое: Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
 
