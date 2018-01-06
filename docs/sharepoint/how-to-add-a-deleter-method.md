---
title: "Как: Добавление метода Deleter | Документы Microsoft"
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
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 622be02def57621f43439f84f84321cb1bac9911
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-deleter-method"></a>Практическое руководство. Добавление метода Deleter
  Пользователь может удалить запись данных из внешнего списка на сайте SharePoint, добавляя можно включить *удаления* метод в модель. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Чтобы создать метод удаления  
  
1.  В конструкторе BDC выберите сущность.  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения об этом окне см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **добавьте метод** выберите **Создание метода удаления**.  
  
     Visual Studio добавляет следующие элементы модели. Эти элементы появляются в **Подробности метода BDC** окна.  
  
    -   Метод с именем **удалить**.  
  
    -   Входной параметр для метода.  
  
    -   Дескриптор типа для параметра.  
  
    -   Экземпляр метода для метода.  
  
     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и нажмите кнопку **Просмотр кода**.  
  
     В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Добавьте код в метод удаления, чтобы удалить запись. Следующий пример удаляет элемент строки из заказа на продажу с помощью образца базы данных AdventureWorks для SQL Server.  
  
    > [!NOTE]  
    >  В данном примере метод использует входные параметры.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  