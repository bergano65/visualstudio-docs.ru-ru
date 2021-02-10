---
title: Интеграция бизнес-данных в SharePoint | Документация Майкрософт
description: Ознакомьтесь с общими сведениями о том, как интегрировать бизнес-данные в SharePoint путем создания модели для службы подключения к бизнес-данным.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94162e2fca66fd86b2ac8b237c518e391d0a9908
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964684"
---
# <a name="integrate-business-data-into-sharepoint"></a>Интеграция бизнес-данных в SharePoint
  Вы можете интегрировать бизнес-данные в SharePoint. Бизнес-данные могут поступать из серверных приложений, таких как [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel и SAP, или из веб-служб. Пользователи могут просматривать, добавлять, обновлять или удалять бизнес-данные с помощью внешних списков или веб-частей бизнес-данных в SharePoint.  Пользователи также могут получать доступ к этим данным в автономном режиме в приложении Microsoft Office, таком как Microsoft Outlook. Дополнительные сведения см. в разделе [Где можно демонстрировать внешние данные](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Чтобы интегрировать данные в SharePoint, создайте модель для службы подключения к бизнес-данным (BDC). Служба BDC — это приложение в SharePoint, которое хранит сведения о данных в бизнес-приложениях. Дополнительные сведения см. в разделе [Служба подключения к бизнес-данным (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Модели в Visual Studio
 Модели в Visual Studio позволяют создавать пользовательский код для извлечения и обновления данных из серверных источников данных. Вы также можете агрегировать данные из нескольких источников данных. Например, можно отобразить список клиентов, содержащий данные из базы данных [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] и веб-службы.

 Кроме того, вы можете импортировать модели, которые уже развернуты в SharePoint. После импорта модели можно добавить пользовательский код или просто использовать Visual Studio для упаковки и развертывания модели в нескольких фермах серверов SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Проектирование модели в Visual Studio
 Модель можно проектировать с помощью конструктора и нескольких окон инструментов. По мере разработки проекта модели Visual Studio создает XML-код модели. Дополнительные сведения см. в [обзоре инструментов проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

 В модели содержатся сущности и методы.

### <a name="entities"></a>Сущности
 Сущность описывает коллекцию полей. Например, сущность может представлять таблицу в базе данных. Сущность отображается как внешний тип содержимого в SharePoint. Дополнительные сведения о внешних типах содержимого см. в разделе [Что такое внешние типы содержимого](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14)).

### <a name="methods"></a>Методы
 Метод позволяет тем, кто использует внешний тип содержимого, выполнять действия с полями сущности. Например, с помощью метода Updater пользователи могут изменять адрес и дату рождения клиента в полях `Address` и `BirthDate` сущности `Customer`.

 Visual Studio создает файл кода службы для каждой сущности в вашей модели. Когда вы добавляете метод в свою модель, Visual Studio создает соответствующий метод в файле кода службы. Добавьте код в каждый метод для выполнения соответствующей задачи. Например, если добавить в модель метод Creator, Visual Studio создаст метод Creator в файле кода службы. Этот метод вызывается службой BDC, когда пользователь нажимает кнопку **Создать элемент** в списке, основанном на данной модели. Поэтому добавьте код в метод Creator, который добавляет новые данные в источник данных. Дополнительные сведения см. в разделе [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)|Описывается процедура создания новой модели иди импорта модели, экспортированной из SharePoint.|
|[Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)|Объясняется, как проектировать элементы модели с помощью инструментов проектирования Visual Studio.|
|[Сравнение конструктора SharePoint и Visual Studio при построении решений с использованием BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Помогает решить, что использовать для создания модели для BDC — Visual Studio или конструктор SharePoint.|
