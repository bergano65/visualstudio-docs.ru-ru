---
title: "Практическое руководство. Добавление метода Updater | Microsoft Docs"
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
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], Обновление"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], обновление данных"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], обновление экземпляров сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], Обновление"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], обновление данных"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], обновление экземпляров сущностей"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Практическое руководство. Добавление метода Updater
  Можно разрешить пользователям обновлять бизнес\-данные во внешнем списке SharePoint, создав метод *обновления*.  Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Создание метода обновления  
  
1.  Выберите сущность в конструкторе BDC.  
  
2.  В строке меню выберите **Вид**, **Другие окна**, **Подробности метода BDC**.  
  
     Откроется окно Подробности метода BDC.  Дополнительные сведения об этом окне см. в разделе [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В списке **Добавить метод** выберите **Создать метод создания**.  
  
     Visual Studio добавит в модель следующие элементы.  Следующие элементы отображаются в окне "Подробности метода BDC".  
  
    -   Метод **Обновить**.  
  
    -   Входной параметр для метода.  
  
    -   Дескриптор типа для параметра.  По умолчанию Visual Studio использует дескриптор типа сущности, определенный в конкретном методе поиска \(например, Contact\).  
  
    -   Экземпляр метода для метода.  
  
     Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Если идентификатора типа сущности представляет поле в таблице базы данных, созданной не автоматически, задайте свойству **Поле средства предобновления** значение **True**.  
  
4.  В **обозревателе решений** откройте контекстное меню файла кода службы, созданного для сущности, затем выберите **Просмотреть код**.  
  
     В редакторе кода открывается файл кода службы сущности.  Дополнительные сведения об этом файле см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Для обновления данных добавьте код в метод обновления.  В следующем примере показано, как обновляются сведения о контакте в примере базы данных AdventureWorks в SQL Server.  
  
    > [!NOTE]  
    >  Замените значение поля `ServerName` на имя сервера.  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  