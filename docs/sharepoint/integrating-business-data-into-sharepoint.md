---
title: Интеграция бизнес-данных в SharePoint | Документация Майкрософт
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e75367844a3a62e044a98f9d52c567fcfca3590e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119919"
---
# <a name="integrate-business-data-into-sharepoint"></a>Интеграция бизнес-данных в SharePoint
  Вы можете интегрировать бизнес-данные в SharePoint. Бизнес-данные могут поступать из внутренних серверных приложений, таких как [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel и SAP, или веб-службы. Пользователей можно просмотреть, добавить, обновить или удалить бизнес-данных с помощью внешних списков или деловых данных веб-частей в SharePoint.  Пользователи также могут работать этот данным в автономном режиме в приложении Microsoft Office, например Microsoft Outlook. Дополнительные сведения см. в разделе [где можно указать внешние данные](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Чтобы интегрировать данные в SharePoint, создайте модель для службы бизнес-данным (BDC). Эта служба представляет приложение в SharePoint, который хранит сведения о данных в бизнес-приложений. Дополнительные сведения см. в разделе [службы бизнес-данным (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Моделей в Visual Studio  
 Моделей в Visual Studio позволяют создавать пользовательский код для извлечения и обновления данных из источников данных. Вы также можете к объединенным данным из нескольких источников данных. Например, можно отобразить список заказчиков, которые содержит данные из [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] базы данных и веб-службы.  
  
 Можно также импортировать моделях, которые уже развернуты в SharePoint. После импорта модели, можно добавить пользовательский код или просто использовать Visual Studio для упаковки и развертывания модели на нескольких фермах серверов SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Разработать модель в Visual Studio
 Для разработки моделей с помощью конструктора и несколькими окнами инструментов. При разработке модели, Visual Studio создает модель XML. Дополнительные сведения см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Модель содержит сущности и методы.  
  
### <a name="entities"></a>Сущности  
 Сущность описывает коллекцию полей. Например сущность может представлять таблицу в базе данных. Сущность отображается в виде внешнего типа содержимого в SharePoint. Дополнительные сведения о внешних типах содержимого см. в разделе [Каковы внешние типы содержимого?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Методы  
 Метод потребители внешнего типа содержимого для выполнения действия с полями сущности. Например, метод обновления может дать пользователям возможность менять адрес и Дата клиента рождения где `Address` и `BirthDate` являются поля `Customer` сущности.  
  
 Visual Studio создает файл кода службы для каждой сущности в модели. При добавлении метода в модель, Visual Studio создает соответствующий метод в файл кода службы. Добавьте код для каждого метода для выполнения соответствующей задачи. Например при добавлении метода Creator в модель, Visual Studio создает метода Creator в файл кода службы. Этот метод вызывается службой BDC, когда пользователь щелкает **новый элемент** кнопки в список, основанный на модели. Таким образом добавьте код в метод Creator, который добавляет новые данные к источнику данных. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>См. также
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)|Показано, как создать новую модель или импорт модели, экспортированные из SharePoint.|  
|[Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)|В этой статье описывается разработка элементы модели с помощью средств разработки Visual Studio.|  
|[Когда следует использовать SharePoint Designer vs. Visual Studio при построении решений с помощью BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Поможет вам решить, следует ли использовать Visual Studio или использовать SharePoint Designer для создания модели для BDC.|  
  
