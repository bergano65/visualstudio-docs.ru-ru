---
title: "Интеграция бизнес-данным в SharePoint | Документы Microsoft"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece3128c2d6850a1d1dd22d0328a4ee2c46da2b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="integrating-business-data-into-sharepoint"></a>Интеграция бизнес-данных в SharePoint
  Можно интегрировать бизнес-данные в SharePoint. Бизнес-данные могут поступать от серверных приложений, таких как [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel и SAP, или веб-службы. Пользователи могут просмотра, добавления, изменения или удаления бизнес-данных с помощью внешних списков или деловых данных веб-частей в SharePoint.  Пользователи могут также доступ к этим данным вне сети, в приложении Microsoft Office, например Microsoft Outlook. Дополнительные сведения см. в разделе [где можно можно показать внешних данных](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Чтобы интегрировать данные в SharePoint, создайте модель для службы бизнес-данным (BDC). Служба BDC — это приложение в SharePoint, в которой хранятся сведения о данных в бизнес-приложениях. Дополнительные сведения см. в разделе [службы бизнес-данным (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Модели в Visual Studio  
 Моделей в Visual Studio позволяют создавать пользовательский код для извлечения и обновления данных из источников данных. Вы также можете статистические данные из нескольких источников данных. Например, можно отобразить список клиентов, содержащий данные из [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] базы данных и веб-службы.  
  
 Можно также импортировать модели, которые уже развернуты в SharePoint. После импорта модели, можно добавить пользовательский код или просто использовать Visual Studio для упаковки и развертывания модели в нескольких фермах серверов SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Проектирование модели в Visual Studio  
 С помощью конструктора и в некоторых окнах инструментов, можно создать модель. При проектировании модели в Visual Studio создает модель XML. Дополнительные сведения см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Модель содержит сущности и методы.  
  
### <a name="entities"></a>Сущности  
 Сущность описывает коллекцию полей. Например сущность может представлять таблицу в базе данных. Сущность отображается в виде типа внешнего содержимого в SharePoint. Дополнительные сведения о типах внешнего содержимого см. в разделе [Каковы внешними типами содержимого?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Методы  
 Метод, который позволяет потребителям внешнего типа содержимого для выполнения действия с полями сущности. Например, метод обновления может предоставить пользователям возможность изменить адрес и создания даты клиента где `Address` и `BirthDate` являются поля `Customer` сущности.  
  
 Visual Studio создает файл кода службы для каждой сущности в модели. При добавлении метода в модель Visual Studio создает соответствующий метод в файл кода службы. Добавьте код для каждого метода для выполнения соответствующих задач. Например при добавлении метода создания модели, Visual Studio создает метод создания в файл кода службы. Этот метод вызывается службой BDC, когда пользователь щелкает **новый элемент** кнопка в виде списка, который основан на модели. Таким образом добавьте код создания метода, который добавляет новые данные в источнике данных. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)|Показано, как создать новую модель или импорт модели, экспортированных из SharePoint.|  
|[Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)|Руководство по разработке элементов модели с помощью средств разработки Visual Studio.|  
|[Когда следует использовать SharePoint Designer vs. Visual Studio при сборке решения, с помощью BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Помогает решить, следует ли использовать Visual Studio или SharePoint Designer для создания модели для BDC.|  
  
  