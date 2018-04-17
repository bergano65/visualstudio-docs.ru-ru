---
title: 'Как: Добавление метода Finder | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b1660d440b72c48787af2cf2c653a420982c8799
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-finder-method"></a>Практическое руководство. Добавление метода Finder
  Чтобы включить службы Business Data Connectivity для отображения списка сущностей в веб-части или списка, необходимо создать *Finder* метод. Метод поиска является специальный метод, который возвращает коллекцию экземпляров сущности. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Чтобы создать метод поиска  
  
1.  В конструкторе BDC выберите сущность.  
  
     Дополнительные сведения см. в разделе [как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения о **Подробности метода BDC** окна, в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **добавьте метод** выберите **создать метод поиска**.  
  
     Visual Studio добавляет метод, возвращаемый параметр и дескриптор типа.  
  
4.  Настройте дескриптор типа как дескриптора типа коллекции сущностей. Дополнительные сведения о создании дескриптора типа коллекции сущностей см. в разделе [как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Необходимо выполнить этот шаг, если сущность был добавлен конкретный метод поиска. Visual Studio использует дескриптор типа, определенного в конкретный метод поиска.  
  
5.  В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и нажмите кнопку **Просмотр кода**. Дополнительные сведения о файле кода службы см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Добавьте код в метод поиска. Этот код выполняет следующие задачи:  
  
    -   Извлекает данные из источника данных.  
  
    -   Возвращает список сущностей в службу BDC.  
  
     В следующем примере возвращается коллекция `Contact` сущностей с использованием данных из образца базы данных AdventureWorks для SQL Server.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>См. также  
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  