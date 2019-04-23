---
title: Разработка решений Office и SharePoint в Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1af1b3ea3f8996d1d9aed2245514c51751f11bc2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112394"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Разработка решений Office и SharePoint в Visual Studio
  Вы можете расширить возможности Microsoft Office и SharePoint, создав облегченное приложение или надстройку, которые пользователи загружают из [Магазина Office](https://store.office.com/) или каталога организации, либо создав решение на основе .NET Framework, которое пользователи устанавливают на компьютерах.

 В этом разделе.

- [Создание надстроек для Office и SharePoint](#Apps)

- [Создание надстройки VSTO](#Add-ins)

- [Создание решения SharePoint](#Solutions)

## <a name="Apps"></a> Создание надстроек для Office и SharePoint
 В Office 2013 и SharePoint 2013 появилась новая модель надстроек, которая помогает создавать, распространять и продавать надстройки, расширяющие возможности Office и SharePoint.  Эти надстройки могут выполняться в Office или SharePoint Online, и пользователи могут работать с ними на разных устройствах.

 Узнайте, как использовать новый [модель надстроек Office](/office/dev/add-ins/overview/office-add-ins) для расширения возможностей Office для пользователей.

 Эти надстройки требуют небольших ресурсов по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  Для начала используйте инструменты разработчика Office для Visual Studio или облегченный набор веб-средств разработки для Office 365 (кодовое имя Napa), который позволяет создавать проекты, писать код и запускать надстройки в браузере.

 ![Приложения для Office и SharePoint концептуальной модели](../vsto/media/officeandsharepointapps2015.png "приложений для Office и SharePoint концептуальной модели")

### <a name="build-an-office-add-in"></a>Создание надстройки Office
 Чтобы расширить функциональные возможности Office, создайте надстройку Office. По сути, это веб-страницы, размещенной в приложении Office, например Excel, Word, Outlook и PowerPoint. Ваше приложение может расширять функциональные возможности документов, таблиц, сообщений электронной почты, встреч, презентаций или проектов.

 Вы можете продавать приложение в Магазине Office.  [Магазин Office](https://store.office.com/) упрощает получение прибыли от надстроек, управление обновлениями и отслеживание телеметрических данных. Приложение также можно опубликовать для пользователей посредством каталога приложений в SharePoint или на сервере Exchange Server.

 Следующее приложение для Office показывает данные листа на карте Bing.

 ![Приложения содержимого для Office](../vsto/media/appforoffice.png "содержимого приложения для Office")

 **Дополнительные сведения**

|Кому|См.|
|--------|---------|
|Узнайте больше о надстройках Office, а затем создайте собственную надстройку.|[Надстройки Office](/office/dev/add-ins/publish/publish)|
|Сравните различные способы расширения возможностей Office и решите, следует ли использовать приложение или надстройку Office.|[Схема действий для надстроек Office, VSTO и VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|

### <a name="build-a-sharepoint-add-in"></a>Создание надстройки SharePoint
 Чтобы расширить возможности SharePoint для пользователей, создайте надстройку SharePoint. Это по сути небольших, простых в использовании автономные приложения, решающие определенные задачи для конкретных бизнес-пользователей.

 Вы можете продавать приложение для SharePoint через [Магазин Office](https://store.office.com/). Надстройку также можно опубликовать для пользователей через каталог надстроек в SharePoint.  Владельцы сайтов могут устанавливать, обновлять и удалять вашу надстройку на своих сайтах SharePoint, не прибегая к помощи администратора фермы серверов или семейства веб-сайтов.

 Ниже приведен пример приложения для SharePoint, которое помогает пользователям управлять деловыми контактами.

 ![Бизнес-приложение диспетчера контактов для SharePoint](../vsto/media/appforsharepoint.png "бизнес-приложение диспетчера контактов для SharePoint")

 **Дополнительные сведения**

|Кому|См.|
|--------|---------|
|Узнайте больше о надстройках SharePoint, а затем создайте собственную надстройку.|[Надстройки SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Сравните надстройки SharePoint с традиционными решениями SharePoint.|[Сравнение надстроек SharePoint с решениями SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Решите, следует ли создать надстройку SharePoint или решение SharePoint.|[Выбор между надстроек SharePoint и решениями SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="Add-ins"></a> Создание надстройки VSTO
 Создание надстройки VSTO для Office 2007 или Office 2010, или для расширения Office 2013 и Office 2016, недоступные в надстройках Office. Надстройки VSTO выполняются только на настольных компьютерах. Пользователям нужно устанавливать надстройки VSTO, поэтому они обычно сложнее в развертывании и поддержке.  Однако надстройку VSTO можно теснее интегрировать с Office. Например, она может добавлять вкладки и элементы управления на ленту Office и выполнять расширенные задачи автоматизации, такие как слияние документов или изменение диаграмм. Вы можете использовать платформу .NET Framework и языки программирования C# и Visual Basic для взаимодействия с объектами Office.

 Ниже приведен пример, какие надстройки VSTO можно сделать. Эта надстройка VSTO добавляет элементы управления ленты, настраиваемую область задач и диалоговое окно в PowerPoint.

 ![Решения PowerPoint надстройки](../vsto/media/powerpointaddin.png "решения-надстройки PowerPoint")

 **Дополнительные сведения**

|Кому|Чтение|
|--------|----------|
|Сравните различные способы расширения возможностей Office и решите, следует ли использовать надстройку VSTO или надстройку Office.|[Схема действий для надстроек Office, VSTO и VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|
|Создание надстройки VSTO.|[Создание настройки VSTO с помощью Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="Solutions"></a> Создание решения SharePoint
 Создайте решение SharePoint для работы с SharePoint Foundation 2010 и SharePoint Server 2010 или реализующее SharePoint 2013 и SharePoint 2016 в за рамки возможностей с помощью надстройки SharePoint.

 Для решений SharePoint требуется локальная ферма серверов SharePoint. Администраторы должны устанавливать их, а так как решения выполняются в SharePoint, они могут повлиять на производительность сервера. Однако решения обеспечивают более широкий доступ к объектам SharePoint. Кроме того, при создании решения SharePoint вы можете использовать платформу .NET Framework и языки программирования C# и Visual Basic для взаимодействия с объектами SharePoint.

 **Дополнительные сведения**

|Кому|См.|
|--------|---------|
|Сравните решения SharePoint с надстройками SharePoint.|[Сравнение надстроек SharePoint с решениями SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Создайте решение SharePoint.|[Создание решений SharePoint](../sharepoint/create-sharepoint-solutions.md)|
