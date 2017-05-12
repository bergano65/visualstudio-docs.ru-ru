---
title: "Практическое руководство. Добавление метода Creator"
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
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление сущностей"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление экземпляров сущностей"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], Создание"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление экземпляров сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], Создание"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Практическое руководство. Добавление метода Creator
  Метод создания добавляет новые данные в источник данных сущности.  Служба подключения к бизнес\-данным вызывает этот метод, если пользователи нажимают кнопку **Новый элемент** на ленте списка, который основан на модели.  Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Добавление метода создания  
  
1.  Выберите сущность в конструкторе BDC.  
  
2.  В строке меню выберите **Вид**, **Другие окна**, **Подробности метода BDC**.  
  
     Откроется окно **Подробности метода BDC**.  Дополнительные сведения об этом окне см. в разделе [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В списке **Добавить метод** выберите **Создать метод создания**.  
  
     Visual Studio добавит в модель следующие элементы, и эти элементы появятся в окне **Подробности метода BDC**.  
  
    -   Метод с именем **Create**.  
  
    -   Входной параметр для метода.  
  
    -   Возвращаемый параметр для метода.  
  
    -   Дескрипторы типа для параметров.  
  
    -   Экземпляр метода для метода.  
  
     Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  В **обозревателе решений** откройте контекстное меню файла кода службы, созданного для сущности, затем выберите **Просмотреть код**.  
  
     В редакторе кода открывается файл кода службы сущности.  Дополнительные сведения о файле с кодом службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  В метод Creator необходимо добавить код, обеспечивающий добавление данных в источник данных.  В следующем примере показано добавление контакта в базу данных AdventureWorks в SQL Server.  
  
    > [!NOTE]  
    >  Замените значение поля `ServerName` на имя сервера.  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  