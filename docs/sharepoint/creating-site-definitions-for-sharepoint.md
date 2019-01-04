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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66e3566b7bfabb7ec2049632937beaa697246403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868330"
---
# <a name="create-site-definitions-for-sharepoint"></a>Создание определений сайтов для SharePoint
  Проект определения сайта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] позволяет создавать *определение узла*, который служит основой для нового сайта SharePoint. Эти определения не только определить внешний вид и поведение сайта SharePoint, но также содержимое по умолчанию и функциональные возможности. В определение можно поместить заранее настроенные списки, типы содержимого, приемники событий, изображения и другие элементы. В SharePoint содержатся определения некоторых сайтов, например блога. При создании сайта, на основе определения сайта БЛОГА, сайт содержит списки веб-частей и другие элементы, которые требует веб-сайту.  
  
 Дополнительные сведения об определениях сайта см. в разделе [шаблоны и определения сайтов](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Проекты определений сайтов
 Проекты определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] содержат только основные файлы, необходимые для сайтов SharePoint; они не предоставляют функциональные возможности по умолчанию. Необходимо добавить файлы и содержимое для предоставления функций, который будет. Сайт можно создавать вручную, путем создания и добавления необходимых файлов.  
  
## <a name="feature-stapling"></a>Средство сшивания компонентов
 Одно из преимуществ создания определений сайтов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] том, что они автоматически использовать *средство сшивания компонентов*. Ассоциация подключает возможность определения узла вместо встраивания его функциональность в само определение сайта. Это позволяет добавить возможность в любой сайт, созданный с помощью определения сайта без изменения исходного определения сайта. Дополнительные сведения см. в разделе [средство сшивания компонентов](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Компоненты проекта определения сайта
 При создании решения определения сайта, добавляются следующие файлы по умолчанию его **SiteDefinition** узла.  
  
|Имя файла|Описание:|  
|---------------|-----------------|  
|*Default.aspx*|Домашняя страница ASPX по умолчанию для нового сайта SharePoint.|  
|*файл onet.XML*|Задает настройки для нового сайта, компоненты шаблона определения сайта и поведение по умолчанию. Эти параметры можно включить атрибуты, такие как типы содержимого, которые включены, в представлениях списка по умолчанию, файлы шаблонов документов и веб-части, включенные в этот сайт. По умолчанию `Modules` раздел содержит список файлов для добавления к сайту SharePoint и как они настроены.|  
|*webtemp_\<SiteDefinitionName > .xml*|Указывает настройки определения сайта, который отображается на **Выбор шаблона** раздел **новый узел SharePoint** страницы.|  
  
 По умолчанию все определения сайтов хранятся в  *\<диск: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* папки. Каждое определение сайта имеется отдельная вложенная папка.  
  
## <a name="related-topics"></a>См. также
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Пошаговое руководство: Создание базового проекта определения сайта](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Пошаговые инструкции по созданию базового проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Практическое руководство. Создание пользовательского определения узла и конфигурации](http://go.microsoft.com/fwlink/?LinkId=183309)|В этой статье описывается создание пользовательского определения узла в SharePoint путем копирования существующего определения сайта и последующего изменения копии.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Описывает исходный файл, задающий настройки определения сайта, доступных в **Выбор шаблона** раздел **новый узел SharePoint** страницы.|  
|[Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|В этой статье описывается подготовка решений SharePoint для глобального использования.|  
|[Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Описывает, как можно создать части на страницу SharePoint, которые пользователи могут изменять.|  
|[Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Описывает, как можно создать многократно используемые элементы управления, которые запускаются в страницы приложений и веб-частей.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Описывает, как использовать конструктор, который появляется при открытии веб-страницы в проекте.|  
|[Общие сведения о веб-страниц ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Содержит общие сведения о структуре [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] веб-страницы, как обрабатываются страниц [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]и как [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страницы отображаются разметку, которая соответствует стандартам XHTML.|  
|[Синтаксисе веб-страниц ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Описание элементов разметки, составляющие страницу ASP.NET.|  
|[Программирование веб-страниц ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Предоставляет сведения о создании обработчиков событий в [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] страниц и способы работы с помощью клиентского скрипта.|  
|[Программирование в Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Описывает использование управляемой объектной модели, которая предоставляется в [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
