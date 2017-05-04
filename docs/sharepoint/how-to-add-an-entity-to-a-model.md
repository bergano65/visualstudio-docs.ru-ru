---
title: "Практическое руководство. Добавление сущности в модель | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление сущности"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], сущность"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление сущности"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], сущность"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Практическое руководство. Добавление сущности в модель
  Чтобы создать сущность, добавьте элемент управления сущности из **панели элементов** Visual Studio в конструктор подключения к бизнес\-данным.  
  
### Добавление сущности в модель  
  
1.  Создайте или откройте проект подключения к бизнес\-данным.  Для получения дополнительной информации см. [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Добавьте элемент управления **Сущность** из группы **Каталог бизнес\-данных** на **панели элементов** в конструктор.  
  
     В конструкторе откроется новая сущность.  Visual Studio добавляет элемент `<Entity>` в XML\-код файла модели подключения к бизнес\-данным соответствующего проекта.  Дополнительные сведения об атрибутах элемента сущности см. в разделе [Entity](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  В конструкторе откройте контекстное меню сущности, выберите **Добавить**, а затем **Идентификатор**.  
  
     В сущности отобразится новый идентификатор.  
  
    > [!NOTE]  
    >  В окне **Свойства** можно изменить имя сущности и идентификатора.  
  
4.  Определите поля сущности в классе.  Можно либо добавить новый класс в проект, либо использовать существующий класс, созданный с помощью других средств, таких как "Реляционный конструктор объектов".  В следующем примере показан класс сущностей с именем Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## См. также  
 [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  