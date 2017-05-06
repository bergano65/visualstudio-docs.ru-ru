---
title: "Практическое руководство. Добавление метода Finder"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], Finder - метод"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], получение сущностей"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], возврат сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], Finder - метод"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], получение сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], возврат сущностей"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Практическое руководство. Добавление метода Finder
  Чтобы включить отображение списка сущностей веб\-части или списка в службе подключения к бизнес\-данным, необходимо создать *метод поиска*.  Метод поиска — это специальный метод, который возвращает коллекцию экземпляров сущностей.  Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Создание метода поиска  
  
1.  Выберите сущность в конструкторе BDC.  
  
     Для получения дополнительной информации см. [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  В строке меню выберите **Вид**, **Другие окна**, **Подробности метода BDC**.  
  
     Откроется окно **Подробности метода BDC**.  Дополнительные сведения об окне **Подробности метода BDC** см. в разделе [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В списке **Добавить метод** выберите **Создать метод поиска**.  
  
     Visual Studio добавляет метод, возвращаемый параметр и дескриптор типа.  
  
4.  Настройте дескриптор типа как дескриптор типа коллекции сущностей.  Дополнительные сведения о создании дескриптора типа коллекции сущностей см. в разделе [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Не обязательно выполнять это действие, если в сущность был добавлен конкретный метод поиска.  Visual Studio использует дескриптор типа, определенный в конкретном методе поиска.  
  
5.  В **обозревателе решений** откройте контекстное меню файла кода службы, созданного для сущности, затем выберите **Просмотреть код**.  Дополнительные сведения о файле кода службы см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Добавьте код в метод поиска.  Этот код выполняет следующие задачи:  
  
    -   Извлекает данные из источника данных.  
  
    -   Возвращает список сущностей в службу BDC.  
  
     В следующем примере показано возвращение коллекции сущностей `Contact` с использованием данных из примера базы данных AdventureWorks в SQL Server.  
  
    > [!NOTE]  
    >  Замените значение поля `ServerName` на имя сервера.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## См. также  
 [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  