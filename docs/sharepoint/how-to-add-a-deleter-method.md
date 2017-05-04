---
title: "Практическое руководство. Добавление метода Deleter | Microsoft Docs"
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
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], Удаление"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление данных"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление экземпляров сущностей"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление данных"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], Удаление"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление данных"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление экземпляров сущностей"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], удаление данных"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Практическое руководство. Добавление метода Deleter
  Можно разрешить конечному пользователю удалять запись данных из внешнего списка на сайте SharePoint, добавив в модель *метод удаления*.  Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Создание метода удаления  
  
1.  Выберите сущность в конструкторе BDC.  
  
2.  В строке меню выберите **Вид**, **Другие окна**, **Подробности метода BDC**.  
  
     Откроется окно **Подробности метода BDC**.  Дополнительные сведения об этом окне см. в разделе [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В списке **Добавить метод** выберите **Создать метод удаления**.  
  
     Visual Studio добавит в модель следующие элементы.  Следующие элементы отображаются в окне **Подробности метода BDC**.  
  
    -   Метод с именем **Delete**.  
  
    -   Входной параметр для метода.  
  
    -   Дескриптор типа для параметра.  
  
    -   Экземпляр метода для метода.  
  
     Для получения дополнительной информации см. [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  В **обозревателе решений** откройте контекстное меню файла кода службы, созданного для сущности, затем выберите **Просмотреть код**.  
  
     В редакторе кода открывается файл кода службы сущности.  Дополнительные сведения о файле с кодом службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Добавьте код в метод удаления, чтобы удалить запись.  В следующем примере показано удаление элемента строки из заказа с использованием примера базы данных AdventureWorks в SQL Server.  
  
    > [!NOTE]  
    >  Метод в данном примере использует входные параметры.  
  
    > [!NOTE]  
    >  Замените значение поля `ServerName` на имя сервера.  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  