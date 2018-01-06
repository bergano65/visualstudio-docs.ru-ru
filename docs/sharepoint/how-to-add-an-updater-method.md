---
title: "Как: Добавление метода Updater | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a03a4038418415889d5394111e0960f0edf01b22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-updater-method"></a>Практическое руководство. Добавление метода Updater
  Можно разрешить пользователям обновлять бизнес-данные во внешнем списке SharePoint, создав *обновления* метод. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Чтобы создать метод обновления  
  
1.  В конструкторе BDC выберите сущность.  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     Откроется окно Подробности метода BDC. Дополнительные сведения об этом окне см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **добавьте метод** выберите **создать метод обновления**.  
  
     Visual Studio добавляет следующие элементы модели. Следующие элементы отображаются в окне Подробности метода BDC.  
  
    -   Метод, который называется **обновление**.  
  
    -   Входной параметр для метода.  
  
    -   Дескриптор типа для параметра. По умолчанию Visual Studio использует дескриптор типа сущности, определенный для метода поиска (например: контакт).  
  
    -   Экземпляр метода для метода.  
  
     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Если идентификатор типа сущности представляет поле в таблице базы данных, который создается автоматически, задайте **поля до обновления** свойства **True**.  
  
4.  В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и нажмите кнопку **Просмотр кода**.  
  
     В редакторе кода открывается файл кода службы сущности. Дополнительные сведения об этом файле см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Добавьте код в метод обновления для обновления данных. В следующем примере обновляется сведения для контакта в образце базы данных AdventureWorks для SQL Server.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  