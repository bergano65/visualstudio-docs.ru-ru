---
title: "Создание страниц для SharePoint | Документы Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4b65c601d36dd04d95466fc8f8dff7a95b70c44a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="creating-pages-for-sharepoint"></a>Создание страниц для SharePoint
  Можно создать страницы приложений, страниц сайта, главных страниц и макетов страниц для сайта SharePoint.  
  
 Страницы приложений можно создать с помощью шаблона в Visual Studio. Создание страниц сайта, главных страниц и макетов страниц с помощью SharePoint Designer. Затем можно импортировать эти страницы в Visual Studio, чтобы использовать их в проекте SharePoint.  
  
 Также можно изменить внешний вид и поведение страниц с помощью каскадных таблиц стилей, ECMAScript и тем.  
  
## <a name="types-of-sharepoint-pages"></a>Типы страниц SharePoint  
 В следующей таблице описаны четыре основных типа страниц, которые содержит сайт SharePoint.  
  
|Тип страницы|Описание:|  
|---------------|-----------------|  
|Страницы приложения|Создание страницы приложения страницу, чтобы содержать пользовательский код или страницу можно было использовать на нескольких сайтах. В противном случае страницу сайта может быть лучшим вариантом.|  
|Страницы сайта|Создание страницы сайта, если необходимо выполнить следующие действия:<br /><br /> -Добавьте страницу в библиотеке SharePoint.<br />-Включите страницы, чтобы узел функции, такие как динамический веб-части и зоны веб-частей.<br />-Пользователи могли настроить страницу с помощью SharePoint Designer.<br /><br /> Не создавать страницу сайта, если страница содержит пользовательский код. Несмотря на то, что пользовательский код можно добавить на страницу сайта, код не будет выполняться, когда пользователь настраивает страницы с помощью SharePoint Designer.|  
|Главные страницы|Создайте главную страницу, чтобы определить общие структуры для страниц сайта и страниц приложения.|  
|Макеты страниц|Макеты страниц относятся к [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] и позволяют определить общие структуры для страниц сайта и страниц приложения.|  
  
 Обзор каждого типа страницы см. в разделе [стандартный блок: страницы и пользовательский интерфейс](http://go.microsoft.com/fwlink/?LinkID=182095), и [макеты страниц и главных страниц](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Создание страниц приложений  
 Страницы приложений в Visual Studio можно создать, добавив **страницы приложения** элемента в проект SharePoint. Можно добавлять элементы управления на страницу и затем обрабатывать события элемента управления путем добавления кода.  
  
 Можно установить точки останова в файле кода страницы, запустить отладчик и тестовую страницу на локальном сайте SharePoint без выполнения дополнительных действий по настройке. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Создание страниц сайта, главных страниц и макетов страниц  
 Можно создать страниц сайта, главных страниц и макетов страниц с помощью SharePoint Designer. Затем можно импортировать эти страницы в Visual Studio. Импорт страниц, чтобы воспользоваться преимуществами развертывания или функций управления исходным кодом, которые доступны в Visual Studio. Дополнительные сведения см. в разделе [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Поскольку это трудно изменить эти страницы после их импорта, следует разрабатывать эти страницы перед их импортом.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Создание каскадных таблиц стилей, ECMAScript и темы  
 Visual Studio предоставляет шаблоны для разработки каскадные таблицы стилей (CSS), ECMAScript (JavaScript, JScript) или файлы тем для сайтов SharePoint. Эти файлы можно создать с помощью руководств в пакет SDK для SharePoint или с помощью средств, таких как SharePoint Designer.  
  
 Эти файлы в решение можно добавить непосредственно или их можно импортировать. В любом случае необходимо создать соответствующие сопоставленные папки для каждого добавляемого элемента. Дополнительные сведения о создании сопоставленных папок см. в разделе [как: Добавление и удаление папок Mapped](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Дополнительные сведения о создании каскадных таблиц стилей см. в разделе [каскадных таблиц стилей листов класс использования в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Дополнительные сведения о создании файлов JavaScript и JScript для решений SharePoint см. в разделе [параметр вверх основные страницу ASPX для ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Дополнительные сведения о темах см. в разделе [стандартный блок: страницы и пользовательский интерфейс](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Описание процедуры добавления страниц приложений: содержимое .aspx, объединенное с главной страницей SharePoint.|  
|[Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)|Показано, как создавать страницы ASP.NET, которые выполняются на сайте SharePoint.|  
|[Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Показано, как для разработки и отладки веб-страницу ASP.NET для сайта SharePoint.|  
  
  