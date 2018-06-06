---
title: Создание определений сайтов SharePoint | Документы Microsoft
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1fae92a9ca958f3d6702ec0f2d1678b33d471bab
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765496"
---
# <a name="create-site-definitions-for-sharepoint"></a>Создание определений сайтов SharePoint
  Проект определения сайта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] позволяет создавать *определения веб-сайта*, который служит основой для нового сайта SharePoint. Эти определения не только определить внешний вид и поведение сайта SharePoint, но также содержимое по умолчанию и функциональные возможности. В определение можно поместить заранее настроенные списки, типы содержимого, приемники событий, изображения и другие элементы. В SharePoint содержатся определения некоторых сайтов, например блога. При создании сайта, на основе определения сайта БЛОГА на сайте представлены списки, веб-части и другие элементы, необходимые для этого типа сайта.  
  
 Дополнительные сведения об определениях сайта см. в разделе [шаблоны сайтов и определения](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Проекты определений сайтов
 Проекты определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] содержат только основные файлы, необходимые для сайтов SharePoint; они не обеспечивают функциональные возможности по умолчанию. Необходимо добавить файлы и содержимое для обеспечения функциональных возможностей, который будет. Можно создать сайт вручную, путем создания и добавления необходимых файлов.  
  
## <a name="feature-stapling"></a>Ассоциации возможности
 Одно из преимуществ создания определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] заключается в том, что они автоматически использоваться *ассоциации возможности*. Ассоциация подключает возможность определения сайта вместо внедрения его функциональность в само определение сайта. Это позволяет добавить возможность в любой сайт, созданный с помощью определения сайта без изменения исходного определения сайта. Дополнительные сведения см. в разделе [ассоциации возможности](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Компоненты проекта определения сайта
 При создании решения определения сайта, добавляются следующие файлы по умолчанию его **SiteDefinition** узла.  
  
|Имя файла|Описание:|  
|---------------|-----------------|  
|*файл Default.aspx*|Домашняя страница ASPX по умолчанию для нового сайта SharePoint.|  
|*файл onet.XML*|Задает конфигурацию нового сайта, компоненты шаблона определения сайта и поведение по умолчанию. Эти параметры можно включить атрибуты, такие как типы содержимого, которые включены, представлениях списка по умолчанию файлы шаблонов документов и веб-части, включенные в этот сайт. По умолчанию `Modules` разделе перечислены файлы, которые будут добавлены на сайт SharePoint и как они настроены.|  
|*XML-файла webtemp_ {SiteDefinitionName}*|Указывает настройки определения сайта, отображающиеся в **Выбор шаблона** раздел **новый сайт SharePoint** страницы.|  
  
 По умолчанию хранятся все определения сайта в *{диска:} \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* папки. Для каждого определения сайта имеет собственную подпапку.  
  
## <a name="related-topics"></a>См. также
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Пошаговое руководство. Создание базового проекта определения сайта](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Пошаговые инструкции по созданию базового проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Как: Создание пользовательского определения узла и конфигурации](http://go.microsoft.com/fwlink/?LinkId=183309)|Описывает, как создать пользовательское определение сайта в SharePoint путем копирования существующего определения сайта и последующего изменения копии.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Описывает исходный файл, задающий настройки определения сайта, доступных в **Выбор шаблона** раздел **новый сайт SharePoint** страницы.|  
|[Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Описывает способ подготовки своих решений SharePoint для глобального использования.|  
|[Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Описывает, как создавать части страницы SharePoint, которые пользователи могут изменять.|  
|[Создание повторно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Описывает, как создавать многократно используемые элементы управления, выполняемых на страницах приложений и веб-частей.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Описывает, как использовать конструктор, который появляется при открытии веб-страницы в проекте.|  
|[Общие сведения о веб-страниц ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Содержит общие сведения о структуре [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] веб-страницы, как обрабатываются страниц [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]и как [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] разметку, которая соответствует стандартам XHTML отображаются на страницах.|  
|[Синтаксис страницы ASP.NET Web](http://go.microsoft.com/fwlink/?LinkId=178727)|Описание элементов разметки, составляющих страницу ASP.NET.|  
|[Программирование веб-страниц ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Содержит сведения о создании обработчиков событий в [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страниц и способах работы с клиентским скриптом.|  
|[Программирование служб Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Описывает использование управляемой объектной модели, которая предоставляется в [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
