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
ms.openlocfilehash: 297ebf0e7c2ed1273dd5a8ac973ce497c4c64781
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986352"
---
# <a name="create-pages-for-sharepoint"></a>Создание страниц для SharePoint
  Можно создавать страницы приложений, страницы сайта, главные страницы и макеты страниц для сайта SharePoint.

 Страницы приложений можно создавать с помощью шаблона в Visual Studio. Создание страниц сайта, главных страниц и макетов страниц с помощью SharePoint Designer. Затем можно импортировать эти страницы в Visual Studio, чтобы использовать их в проекте SharePoint.

 Можно также изменять внешний вид и поведение страниц с помощью каскадных таблиц стилей, ECMAScript и тем.

## <a name="types-of-sharepoint-pages"></a>Типы страниц SharePoint
 В следующей таблице описаны четыре основных типа страниц, которые содержит сайт SharePoint.

|Тип страницы|Описание|
|---------------|-----------------|
|Страницы приложения|Создайте страницу приложения, если требуется, чтобы страница содержала пользовательский код или вы хотите, чтобы страница была общей для нескольких сайтов. В противном случае лучшим выбором может быть страница сайта.|
|Страницы сайта|Создайте страницу сайта, если необходимо выполнить следующие задачи.<br /><br /> — Добавьте страницу в библиотеку SharePoint.<br />-Включите на странице возможности размещения таких функций, как динамическая веб-части и зоны веб-частей.<br />— Разрешить пользователям настраивать страницу с помощью SharePoint Designer.<br /><br /> Не создавайте страницу сайта, если требуется, чтобы страница содержала пользовательский код. Несмотря на то, что на страницу сайта можно добавить пользовательский код, выполнение кода прекращается, когда пользователь настраивает страницу с помощью SharePoint Designer.|
|Главные страницы|Создайте главную страницу, если необходимо определить общую структуру страниц сайта и страниц приложений.|
|Макеты страниц|Макеты страниц зависят от [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] и позволяют дополнительно определять общую структуру страниц сайта и страниц приложений.|

 Общие сведения о каждом типе страницы см. в разделе [стандартный блок: страницы, Пользовательский интерфейс](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)), [макеты страниц и главные страницы](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Создание страниц приложения
 Вы можете создавать страницы приложений в Visual Studio, добавляя элемент **страницы приложения** в проект SharePoint. На страницу можно добавлять элементы управления, а затем управлять событиями элементов управления путем добавления кода.

 Можно задать точки останова в файле кода страницы, запустить отладчик и проверить страницу на локальном сайте SharePoint, не выполняя никаких дополнительных действий по настройке. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Создание страниц сайта, главных страниц и макетов страниц
 С помощью SharePoint Designer можно создавать страницы сайта, главные страницы и макеты страниц. Затем можно импортировать эти страницы в Visual Studio. Импортируйте страницы, если хотите воспользоваться преимуществами функций развертывания или управления версиями, доступных в Visual Studio. Дополнительные сведения см. в разделе [Импорт элементов с существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Поскольку эти страницы сложно изменить после импорта, эти страницы следует спроектировать перед импортом.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Создание каскадных таблиц стилей, ECMAScript и тем
 Visual Studio не предоставляет шаблоны для разработки каскадные таблицы стилей (CSS), ECMAScript (JavaScript, JScript) или файлов темы для сайтов SharePoint. Эти файлы можно создать с помощью руководств, доступных в пакете SDK для SharePoint, или с помощью таких средств, как SharePoint Designer.

 Вы можете добавить эти файлы в решение напрямую или импортировать их. В любом случае необходимо создать соответствующие сопоставленные папки для каждого добавляемого элемента. Дополнительные сведения о создании сопоставленной папки см. в разделе [инструкции. Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Дополнительные сведения о создании каскадные таблицы стилей см. [в разделе Использование класса каскадные таблицы стилей в SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Дополнительные сведения о создании файлов JavaScript и JScript для решения SharePoint см. в разделе [Настройка базовой страницы ASPX для ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Дополнительные сведения о темах см. [в разделе Стандартный блок: страницы и пользовательский интерфейс](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Создание страниц приложения для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Описывает добавление страниц приложений: содержимое *ASPX* , объединенное с главной страницей SharePoint.|
|[Как создать страницу приложения](../sharepoint/how-to-create-an-application-page.md)|Показывает, как создавать страницы ASP.NET, которые выполняются на сайте SharePoint.|
|[Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Демонстрируется разработка и отладка веб-страницы ASP.NET для сайта SharePoint.|
