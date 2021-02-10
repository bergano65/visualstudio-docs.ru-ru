---
title: Создание страниц для SharePoint | Документация Майкрософт
description: Создавайте страницы приложений для SharePoint с помощью шаблона в Visual Studio. Создавайте страницы сайта, эталонные страницы и макеты страниц с помощью SharePoint Designer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 702d2c4d5cafd6f4ff4ef2e4104da9f6cc02c5fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949172"
---
# <a name="create-pages-for-sharepoint"></a>Создание страниц для SharePoint
  Вы можете создавать страницы приложений, страницы сайта, эталонные страницы и макеты страниц для сайта SharePoint.

 Страницы приложений можно создавать с помощью шаблона в Visual Studio. Страницы сайта, эталонные страницы и макеты страниц создаются с помощью SharePoint Designer. Затем страницы можно импортировать в Visual Studio, чтобы использовать их в проекте SharePoint.

 Вы также можете изменять внешний вид и поведение страниц с помощью каскадных таблиц стилей, ECMAScript и тем.

## <a name="types-of-sharepoint-pages"></a>Типы страниц SharePoint
 В приведенной ниже таблице описаны четыре основных типа страниц, которые содержит сайт SharePoint.

|Тип страницы|Описание|
|---------------|-----------------|
|Страницы приложения|Создайте страницу приложения, если требуется, чтобы страница содержала пользовательский код или использовалась на нескольких сайтах. В противном случае лучше будет выбрать страницу сайта.|
|Страницы сайта|Создайте страницу сайта, если необходимо выполнить какие-либо из следующих задач:<br /><br /> — добавить страницу в библиотеку SharePoint;<br />— разместить на странице такие компоненты, как динамические веб-части и зоны веб-частей;<br />— дать пользователям возможность настраивать страницу с помощью SharePoint Designer.<br /><br /> Не создавайте страницу сайта, если страница должна содержать пользовательский код. Хотя на страницу сайта можно добавить пользовательский код, его выполнение прекращается, когда пользователь настраивает страницу с помощью SharePoint Designer.|
|Эталонные страницы|Создайте эталонную страницу, если необходимо определить общую структуру для страниц сайта и страниц приложений.|
|Макеты страниц|Макеты страниц относятся к [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] и позволяют дополнительно настраивать общую структуру для страниц сайта и страниц приложений.|

 Общие сведения о каждом типе страниц см. в статьях [Стандартный блок: страницы и пользовательский интерфейс](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) и [Макеты страниц и главные страницы](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Создание страниц приложений
 Вы можете создавать страницы приложений в Visual Studio, добавляя элемент **Страница приложения** в проект SharePoint. На страницу можно добавить элементы управления, а затем код для обработки их событий.

 В файле кода страницы можно установить точки останова, запустить отладчик и протестировать страницу на локальном сайте SharePoint, не выполняя никаких дополнительных действий по настройке. Дополнительные сведения см. в статье [Создание страниц приложения для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Создание страниц сайта, эталонных страниц и макетов страниц
 Страницы сайта, эталонные страницы и макеты страниц можно создавать с помощью SharePoint Designer. Затем эти страницы можно импортировать в Visual Studio. Импортируйте страницы, если хотите воспользоваться функциями развертывания или управления исходным кодом, доступными в Visual Studio. Дополнительные сведения см. в статье [Импорт элементов с существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Так как эти страницы сложно изменить после импорта, их следует полностью спроектировать перед импортом.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Создание каскадных таблиц стилей, ECMAScript и тем
 В Visual Studio нет шаблонов для разработки каскадных таблиц стилей (CSS), ECMAScript (JavaScript, JScript) или файлов тем для сайтов SharePoint. Эти файлы можно создать, следуя инструкциям из пакета SDK для SharePoint, или с помощью таких средств, как SharePoint Designer.

 Добавить их в решение можно напрямую или путем импорта. В любом случае необходимо создать соответствующие сопоставленные папки для каждого добавляемого элемента. Дополнительные сведения о создании сопоставленных папок см. в статье [Практическое руководство. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Дополнительные сведения о создании каскадных таблиц стилей см. в статье [Использование класса каскадных таблиц стилей в SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Дополнительные сведения о создании файлов JavaScript и JScript для решений SharePoint см. в статье [Настройка страницы приложения для ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Дополнительные сведения о темах см. в статье [Стандартный блок: страницы и пользовательский интерфейс](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Описывается добавление страниц приложений: файлов *ASPX* содержимого, объединяемых с эталонной страницей SharePoint.|
|[Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)|Демонстрируется создание страниц ASP.NET, которые выполняются на сайте SharePoint.|
|[Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Демонстрируется разработка и отладка веб-страниц ASP.NET для сайта SharePoint.|
