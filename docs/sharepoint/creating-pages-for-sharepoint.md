---
title: Создание страниц для SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62419893"
---
# <a name="create-pages-for-sharepoint"></a>Создание страниц для SharePoint
  Можно создать страницы приложений, страниц узла, главных страниц и макетов страниц для сайта SharePoint.

 Страницы приложений можно создать с помощью шаблона в Visual Studio. Создание страницы сайта, главных страниц и макетов страниц с помощью SharePoint Designer. Затем можно импортировать эти страницы в Visual Studio, чтобы использовать их в проекте SharePoint.

 Также можно изменить внешний вид и поведение страниц с помощью каскадных таблиц стилей, ECMAScript и темы.

## <a name="types-of-sharepoint-pages"></a>Типы страниц SharePoint
 Ниже перечислены четыре основных типа страниц, которые содержит сайт SharePoint.

|Тип страницы|Описание|
|---------------|-----------------|
|Страницы приложения|Создание страницы приложения, если страница должна содержать пользовательский код или страница должна быть общими для нескольких сайтов. В противном случае страницу сайта может быть лучшим выбором.|
|Страницы сайта|Создайте страницу сайта, если вы хотите выполнять следующие задачи:<br /><br /> -Страница добавления в библиотеку SharePoint.<br />— Включите страницы, чтобы компоненты узла, такие как динамический веб-частей и зоны веб-частей.<br />— Разрешить пользователям настраивать страницы с помощью SharePoint Designer.<br /><br /> Не следует создавать страницу сайта, если страница должна содержать пользовательский код. Несмотря на то, что пользовательский код можно добавить на страницу сайта, код не будет выполняться, когда пользователь настраивает страницы с помощью SharePoint Designer.|
|Главные страницы|Создание главной страницы, чтобы определить общие структуры для страниц узла и страницы приложений.|
|Макеты страниц|Макеты страниц относятся к [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] и позволяют определить общие структуры для страниц узла и страницы приложений.|

 Обзор каждого типа страницы, см. в разделе [стандартный блок: Страницы и пользовательский интерфейс](http://go.microsoft.com/fwlink/?LinkID=182095), и [макетов страниц и главные страницы](http://go.microsoft.com/fwlink/?LinkID=182096).

## <a name="create-application-pages"></a>Создание страницы приложения
 Страницы приложений можно создать в Visual Studio, добавив **страницы приложения** элемента в проект SharePoint. Можно добавлять элементы управления на страницу и затем обрабатывать события элемента управления путем добавления кода.

 Можно установить точки останова в файле кода страницы, запустить отладчик и проверить страницу на локальном сайте SharePoint без выполнения дополнительных действий по настройке. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Создание страницы сайта, главных страниц и макетов страниц
 Можно создать страниц узла, главных страниц и макетов страниц с помощью SharePoint Designer. Затем можно импортировать эти страницы в Visual Studio. Импорт страниц, если вы хотите воспользоваться преимуществами развертывания или функций системы управления версиями, доступные в Visual Studio. Дополнительные сведения см. в разделе [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Так как это трудно изменить эти страницы, после их импорта, прежде чем импортировать их следует разрабатывать эти страницы.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Создание каскадных таблиц стилей, ECMAScript и темы
 Visual Studio предоставляет шаблоны для разработки каскадных таблиц стилей (CSS), ECMAScript (JavaScript, JScript) или файлы тем для сайтов SharePoint. Эти файлы можно создать с помощью руководств в пакете SDK для SharePoint или с помощью средств, таких как SharePoint Designer.

 Эти файлы в решение можно добавить непосредственно, или вы можете импортировать их. В любом случае необходимо создать соответствующие сопоставленные папки для каждого добавляемого элемента. Дополнительные сведения о том, как создать сопоставленную папку см. в разделе [как: Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Дополнительные сведения о создании каскадных таблиц стилей, см. в разделе [каскадных листы класс использования стилей в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Дополнительные сведения о создании файлов JavaScript и JScript для решений SharePoint см. в разделе [параметр вверх страницы приложения для ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Дополнительные сведения о темах см. в разделе [стандартный блок: Страницы и пользовательский интерфейс](http://go.microsoft.com/fwlink/?LinkID=182095).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Описывает способы добавления страниц приложений: *.aspx* содержимое, объединенное с эталонной страницей SharePoint.|
|[Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)|Показано, как создавать страницы ASP.NET, которые выполняются на сайте SharePoint.|
|[Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Показано, как для разработки и отладки веб-страницу ASP.NET для сайта SharePoint.|
