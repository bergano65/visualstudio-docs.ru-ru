---
title: 'Способ: добавить конкретный метод поиска | Документы Microsoft'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d00159a8c944944348e4eec5fb98aaa4d6e9bae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-specific-finder-method"></a>Практическое руководство. Добавление определенного метода Finder
  Можно вернуть единственный экземпляр сущности, создав *конкретный* метод. Служба бизнес-данным (BDC), выполняет конкретный метод, при выборе сущности в веб-части бизнес-данных или внешний список. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-specific-finder-method"></a>Чтобы создать конкретный метод поиска  
  
1.  В конструкторе BDC выберите сущность.  
  
     Сведения о том, как добавить сущность в конструкторе BDC в Visual Studio см. в разделе [как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения об этом окне см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **добавьте метод** выберите **создать конкретный метод поиска**.  
  
     Visual Studio добавляет следующие элементы модели. Эти элементы появляются в **Подробности метода BDC** окна.  
  
    -   Метод.  
  
    -   Входной параметр для метода.  
  
    -   Возвращаемый параметр для метода.  
  
    -   Дескриптор типа для каждого параметра.  
  
    -   Экземпляр метода для метода.  
  
     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Откройте Visual Studio **свойства** окна.  
  
5.  Настройте дескриптор типа как возвращаемый параметр как дескриптора типа сущности. Сведения о создании дескриптора типа сущности см. в разделе [как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Выполняйте этот шаг, если сущность был добавлен метод поиска не нужно. Visual Studio использует дескриптор типа, определенного в методе поиска.  
  
    > [!NOTE]  
    >  Если поле идентификатора типа сущности представляет поле в таблице базы данных, который создается автоматически, задайте **только для чтения** поля идентификатора значение **True**.  
  
6.  В **сведения о методе** окно, выберите экземпляр для данного метода.  
  
7.  В **окно свойств**, задайте **имя возвращаемого параметра** на имя возвращаемого параметра метода. Дополнительные сведения о свойствах экземпляра метода см. в разделе [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и нажмите кнопку **Просмотр кода**.  
  
     В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Добавьте код в конкретный метод поиска. Этот код выполняет следующие задачи:  
  
    -   Извлекает записи из источника данных.  
  
    -   Возвращает сущности в службу BDC.  
  
     В следующем примере возвращается контакта из образца базы данных AdventureWorks для SQL Server.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="see-also"></a>См. также  
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)  
  
  