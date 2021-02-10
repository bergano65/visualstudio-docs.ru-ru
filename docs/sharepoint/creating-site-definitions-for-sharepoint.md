---
title: Создание определений сайтов SharePoint | Документация Майкрософт
description: Создавайте определения сайтов SharePoint. Определения сайтов задают внешний вид и поведение сайта SharePoint, а также его содержимое и функциональные возможности по умолчанию.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c802832a9881cf3bf247c8e48b8ecdc2d784b1c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949016"
---
# <a name="create-site-definitions-for-sharepoint"></a>Создание определений сайтов SharePoint
  Проект определения сайта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] позволяет создать *определение сайта*, которое будет служить основой для нового сайта SharePoint. Эти определения задают не только внешний вид и поведение сайта SharePoint, но и его содержимое и функциональные возможности по умолчанию. В определение можно поместить заранее настроенные списки, типы содержимого, приемники событий, изображения и другие элементы. В SharePoint содержатся определения некоторых сайтов, например блога. При создании сайта на основе определения BLOG сайт содержит списки, веб-части и другие элементы, необходимые для ведения блога.

 Дополнительные сведения об определениях сайта см. в разделе [Шаблоны и определения сайтов](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Проекты определений сайтов
 Проекты определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] предоставляют только базовые файлы, необходимые сайту SharePoint; они не предоставляют никакие функциональные возможности по умолчанию. Чтобы обеспечить необходимые функциональные возможности, вы должны добавить файлы и содержимое. Сайт можно создать вручную, создавая и добавляя необходимые файлы.

## <a name="feature-stapling"></a>Ассоциация возможности
 Одно из преимуществ создания определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] заключается в том, что они автоматически используют *ассоциацию возможности*. Ассоциация возможности присоединяет возможность к определению сайта, а не внедряет ее функциональность в само определение сайта. Таким образом можно добавлять эту возможность на любой сайт, созданный с помощью определения сайта, не изменяя исходное определение сайта. Дополнительные сведения см. в разделе [Ассоциация возможности](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Компоненты проектов определений сайтов
 При создании решения для определения сайта в его узел **SiteDefinition** добавляются следующие файлы по умолчанию.

|Имя файла|Описание|
|---------------|-----------------|
|*default.aspx*|Домашняя страница ASPX по умолчанию для нового сайта SharePoint.|
|*onet.xml*|Задает конфигурацию нового сайта, компоненты шаблона определения сайта и поведение по умолчанию. Эти параметры могут содержать такие атрибуты, как разрешенные типы содержимого, представления списков по умолчанию, файлы шаблонов документов и веб-части, включенные в сайт. По умолчанию в разделе `Modules` перечислены файлы, добавляемые на сайт SharePoint, и сведения об их настройке.|
|*webtemp_\<SiteDefinitionName>.xml*|Задает настройки определения сайта, которые находятся в разделе **Выбор шаблона** страницы **Создание сайта SharePoint**.|

 По умолчанию все определения сайтов хранятся в папке *\<drive:>\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates*. Каждое определение сайта находится в собственной вложенной папке.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Пошаговое руководство. Создание базового проекта определения сайта](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Пошагово описывается создание базового проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Практическое руководство. Создание настраиваемого определения и конфигурации сайта](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Описывается создание настраиваемого определения сайта в SharePoint путем копирования существующего определения сайта и последующего изменения этой копии.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Описывается исходный файл, задающий определения сайта, которые находятся в разделе **Выбор шаблона** страницы **Создание сайта SharePoint**.|
|[Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Описывается подготовка решений SharePoint для использования во всем мире.|
|[Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Описывается процесс создания частей страницы SharePoint, которые пользователи могут изменять.|
|[Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Описывается процесс создания многократно используемых элементов управления, которые работают на страницах приложений и в веб-частях.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Описывается порядок использования конструктора, который появляется при открытии веб-страницы в проекте.|
|[Общие сведения о веб-страницах ASP.NET](/previous-versions/aspnet/428509ah(v=vs.100))|Общие сведения о структуре веб-страниц [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], о том, как [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] обрабатывает страницы, и как страницы [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] отображают разметку, которая соответствует стандартам XHTML.|
|[Синтаксис веб-страниц ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Описываются элементы разметки, составляющие страницу ASP.NET.|
|[Программирование веб-страниц ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Сведения о создании обработчиков событий на страницах [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] и о работе с клиентскими сценариями.|
|[Программирование в Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Описывается порядок использования управляемой объектной модели, которая предоставляется в [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
