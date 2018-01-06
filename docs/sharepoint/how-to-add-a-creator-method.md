---
title: "Как: Добавление метода Creator | Документы Microsoft"
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95c98887e50786df4e59010070064eaeb6bafa0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-creator-method"></a>Практическое руководство. Добавление метода Creator
  Метод создания добавляет новые данные в источник данных сущности. Служба бизнес-данным (BDC) вызывает этот метод, если пользователь решил **новый элемент** кнопки на ленте списка, который основан на модели. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Добавление метода Creator  
  
1.  В конструкторе BDC выберите сущность.  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения об этом окне см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **добавьте метод** выберите **создать метод**.  
  
     Visual Studio добавляет следующие элементы модели, и эти элементы появляются в **Подробности метода BDC** окна.  
  
    -   Метод с именем **создать**.  
  
    -   Входной параметр для метода.  
  
    -   Возвращаемый параметр для метода.  
  
    -   Дескрипторы для параметров типа.  
  
    -   Экземпляр метода для метода.  
  
     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и нажмите кнопку **Просмотр кода**.  
  
     В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Добавьте код создания метода, который добавляет данные в источник данных. В следующем примере добавляется контакта с образцом базы данных AdventureWorks для SQL Server.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  