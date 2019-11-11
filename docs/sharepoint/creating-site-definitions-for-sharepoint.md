---
title: Создание определений сайтов для SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a75b7143412d360a7663e7cf94a1244d66d15a2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984526"
---
# <a name="create-site-definitions-for-sharepoint"></a>Создание определений сайтов для SharePoint
  Проект определения сайта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] позволяет создать *Определение сайта*, которое служит основой для нового сайта SharePoint. Эти определения не только определяют внешний вид и поведение сайта SharePoint, но и его содержимое и функциональные возможности по умолчанию. В определении можно разместить предварительно настроенные списки, типы содержимого, приемники событий, изображения и другие элементы. В SharePoint содержатся определения некоторых сайтов, например блога. При создании сайта на основе определения сайта блога сайт содержит списки, веб-части и другие элементы, необходимые сайту блога.

 Дополнительные сведения об определениях сайтов см. в разделе [шаблоны сайтов и определения](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Проекты определений сайтов
 Проекты определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] предоставляют только основные файлы, необходимые сайту SharePoint; они не предоставляют никаких функциональных возможностей по умолчанию. Чтобы предоставить необходимые функции, необходимо добавить файлы и содержимое. Вы можете создать сайт вручную, создав и добавив необходимые файлы.

## <a name="feature-stapling"></a>Ассоциация компонентов
 Одно из преимуществ создания определений узлов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] заключается в том, что они автоматически используют *Прикрепление компонентов*. Ассоциация признаков присоединяет функцию к определению сайта, а не внедряет ее функциональность в само определение сайта. Это позволяет добавить эту функцию на любой сайт, созданный с помощью определения сайта, не изменяя исходное определение сайта. Дополнительные сведения см. в разделе [Ассоциация компонентов](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Компоненты проекта определения сайта
 При создании решения для определения сайта в его узел **ситедефинитион** добавляются следующие файлы по умолчанию.

|Имя файла|Описание|
|---------------|-----------------|
|*Default. aspx*|Домашняя страница ASPX по умолчанию для нового сайта SharePoint.|
|*Onet. XML*|Задает конфигурацию нового сайта, компоненты шаблона определения сайта и поведение по умолчанию. Эти параметры могут включать такие атрибуты, как включенные типы содержимого, представления списков по умолчанию, файлы шаблонов документов и веб-части, включенные в сайт. По умолчанию в разделе `Modules` перечислены файлы, добавляемые на сайт SharePoint и способ их настройки.|
|*webtemp_\<Ситедефинитионнаме >. XML*|Задает конфигурации определения сайта, которые отображаются в разделе " **Выбор шаблона** " на странице " **Создание сайта SharePoint** ".|

 По умолчанию все определения сайтов хранятся в папке *\<диск: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* . Каждое определение сайта имеет собственную вложенную папку.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Пошаговое руководство. Создание базового проекта определения сайта](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Приводится пошаговое описание создания базового проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Как создать пользовательское определение и конфигурацию сайта](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Описывает создание пользовательского определения сайта в SharePoint путем копирования существующего определения сайта и последующего изменения копии.|
|[*Файл. XML*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Описывает исходный файл, в котором указаны определения сайтов, доступные в разделе « **Выбор шаблона** » на странице « **Создание сайта SharePoint** ».|
|[Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Описывает подготовку решений SharePoint для глобального использования.|
|[Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Описывает, как можно создавать части страницы SharePoint, которые пользователи могут изменять.|
|[Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Описание процесса создания многократно используемых элементов управления, которые выполняются на страницах приложений и веб-части.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Описывает использование конструктора, отображаемого при открытии веб-страницы в проекте.|
|[Обзор веб-страницы ASP.NET](/previous-versions/aspnet/428509ah(v=vs.100))|Содержит общие сведения о структуре [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] веб-страниц, о том, как страницы обрабатываются [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]и как [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницы отображают разметку, которая соответствует стандартам XHTML.|
|[Синтаксис веб-страницы ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Описывает элементы разметки, которые составляют страницу ASP.NET.|
|[Веб-страницы ASP.NET программирования](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Содержит сведения о создании обработчиков событий на [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницах и о работе с клиентским скриптом.|
|[Программирование в службах Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Описывает, как использовать управляемую объектную модель, предоставляемую в [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>См. также
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
