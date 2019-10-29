---
title: Интеграция бизнес-данных в SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986394"
---
# <a name="integrate-business-data-into-sharepoint"></a>Интеграция бизнес-данных в SharePoint
  Бизнес-данные можно интегрировать в SharePoint. Бизнес-данные могут поступать из серверных приложений, таких как [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel, SAP или веб-служба. Пользователи могут просматривать, добавлять, обновлять или удалять бизнес-данные с помощью внешних списков или бизнес-данных веб-части в SharePoint.  Пользователи также могут получать доступ к этим данным в автономном режиме в Microsoft Office приложении, таком как Microsoft Outlook. Дополнительные сведения см. в разделе [где можно показать внешние данные](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Чтобы интегрировать данные в SharePoint, создайте модель для службы подключения к бизнес-данным (BDC). Служба BDC — это приложение в SharePoint, которое хранит сведения о данных в бизнес-приложениях. Дополнительные сведения см. в разделе [Служба подключения к бизнес-данным (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Модели в Visual Studio
 Модели в Visual Studio позволяют писать пользовательский код для получения и обновления данных из серверных источников данных. Можно также выполнять агрегирование данных из нескольких источников данных. Например, можно отобразить список клиентов, содержащих данные из [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] базы данных и веб-службы.

 Также можно импортировать модели, которые уже развернуты в SharePoint. После импорта модели можно добавить пользовательский код или просто использовать Visual Studio для упаковки и развертывания модели в нескольких фермах серверов SharePoint. Дополнительные сведения см. [в статье Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Проектирование модели в Visual Studio
 Модель можно спроектировать с помощью конструктора и нескольких окон инструментов. При проектировании модели Visual Studio создает XML-код модели. Дополнительные сведения см. в статье [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Модель содержит сущности и методы.

### <a name="entities"></a>Сущности
 Сущность, описывающая коллекцию полей. Например, сущность может представлять таблицу в базе данных. Сущность отображается как внешний тип содержимого в SharePoint. Дополнительные сведения о типах внешних содержимого см. в разделе [что такое внешние типы содержимого?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Методы
 Метод позволяет потребителям внешнего типа содержимого выполнять действия с полями сущности. Например, метод обновления может позволить пользователям изменить адрес и дату рождения клиента, где `Address` и `BirthDate` являются полями `Customer` сущности.

 Visual Studio создает файл кода службы для каждой сущности в модели. При добавлении метода в модель Visual Studio создает соответствующий метод в файле кода службы. Добавьте код в каждый метод, чтобы выполнить соответствующую задачу. Например, если добавить в модель метод Creator, Visual Studio создаст метод Creator в файле кода службы. Этот метод вызывается службой BDC, когда пользователь нажимает кнопку **создать элемент** в списке, основанном на модели. Поэтому добавьте код в метод Creator, который добавляет новые данные в источник данных. Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)|Показывает, как создать новую модель или импортировать модель, экспортируемую из SharePoint.|
|[Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)|Описывает, как проектировать элементы модели с помощью средств проектирования Visual Studio.|
|[Когда следует использовать SharePoint Designer и Visual Studio при создании решений с помощью BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Помогает решить, следует ли использовать Visual Studio или использовать SharePoint Designer для создания модели для BDC.|
