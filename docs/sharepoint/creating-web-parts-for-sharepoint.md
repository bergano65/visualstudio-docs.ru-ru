---
title: Создание веб-частей для SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 882c2edfc097b8da57cc26c431cbaaa72ba200b6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691536"
---
# <a name="creating-web-parts-for-sharepoint"></a>Создание веб-частей для SharePoint
  С помощью веб-частей, можно изменить содержимое, внешний вид и поведение страниц сайта SharePoint с помощью браузера. Веб-части, серверные элементы управления, которые выполняются в страницу веб-частей: они являются составными частями страниц, которые отображаются на сайте SharePoint. В разделе [стандартный блок: веб-части](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Можно создать и отлаживать веб-частей на сайте SharePoint с помощью шаблонов из Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Создание веб-части в Visual Studio
 Создание веб-части путем добавления **веб-часть** элемента в любой проект SharePoint. Можно использовать **веб-часть** элемента в изолированное решение или решение фермы.  
  
 Если необходимо визуально разработать веб-часть с помощью конструктора, создайте **визуальной веб-части** или добавьте **Визуальная веб-часть** элемента в любой проект SharePoint. Можно использовать **Визуальная веб-часть** элемента только решения фермы.  
  
### <a name="web-part-item"></a>Элемент веб-части
 Объект **веб-часть** элемента содержит файлы, которые можно использовать для разработки веб-части для сайта SharePoint. При добавлении **веб-часть** элемента, Visual Studio создает папку в проекте и добавляет в нее несколько файлов. В следующей таблице описаны каждого файла.  
  
|Файл|Описание:|  
|----------|-----------------|  
|Файл Elements.XML|Содержит сведения, используемые файлом определения компонента в проекте для развертывания веб-части.|  
|файл .webpart|Предоставляет сведения, необходимые для отображения веб-части в веб-частей SharePoint.|  
|Файл кода|Содержит методы, которые добавляют элементы управления веб-части и, создающие пользовательское содержимое внутри веб-части.|  
  
 Дополнительные сведения см. в разделе [как: Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Элемент Visual веб-части
 Визуальная веб-часть имеет веб-части, создаваемом с помощью конструктора Visual Web Developer в Visual Studio. Визуальная веб-часть работает так же, как веб-часть. Чтобы добавить элементы управления, такие как кнопки и текстовые поля, веб-часть, добавьте код в XML-файл. Тем не менее, добавлении элементов управления в визуальной веб-части, перетащив или скопировав их на веб-части из Visual Studio **элементов**. Затем конструктор создает требуемый код в XML-файле. В разделе [как: Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Элементы управления SharePoint
 Visual Studio предоставляет некоторые элементы управления для создания страницы SharePoint, например страниц приложений. Эти элементы управления отображаются в **элементов** под **элементы управления SharePoint**. Функциональные возможности этих элементов управления является производным от [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) имен, содержащее ASP.NET серверных элементов управления, используемые на страницах сайты и списки SharePoint.  
  
|Имя элемента|Описание:|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Вставляет ASP меню. Дополнительные сведения см. в разделе [Обзор элемента управления меню](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Вставляет **ССЫЛКУ** на странице ASPX элемента и применяет один или несколько внешних таблицах стилей определяется **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Вставляет элемент управления даты и времени в ASPX-страницы.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Вставляет проверки безопасности в ASPX-страницы|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Возвращает свойство из указанного списка.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Возвращает глобальные свойства текущего веб-сайта.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Вставляет ссылку на RSS-канал в ASPX-страницы.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Предоставляет свойства и методы для регистрации ресурсы, такие как сценарии, на странице, чтобы они могут быть запрошены при отображении страницы.|  
|[Тема](http://go.microsoft.com/fwlink/?LinkId=235314)|Применяет тему ASPX-страницу.|  
  
## <a name="debug-a-web-part"></a>Отладка веб-части
 Можно отлаживать проект SharePoint, который содержит веб-части, так же, как отладка других проектов Visual Studio. При запуске отладчика Visual Studio, Visual Studio откроется сайт SharePoint.  
  
 Чтобы начать отладку кода, добавьте веб-части на страницу веб-частей в SharePoint.  
  
 Дополнительные сведения об отладке проектов SharePoint см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Ограничения части Visual web
 Начиная с Visual Studio, можно добавить визуальных веб-частей для изолированного решения SharePoint и решениями фермы. Тем не менее визуальные веб-части имеют следующие ограничения:  
  
-   Визуальные веб-части не поддерживают подстановочные параметры. Дополнительные сведения см. в разделе [подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
-   Пользовательские элементы управления или визуальных веб-частей нельзя перетащить и удалить или скопировать в визуальных веб-частей. Это действие приводит к ошибке построения.  
  
-   Визуальные веб-части напрямую не поддерживается токены SharePoint server, например $SPUrl. Дополнительные сведения см. в разделе «Токена ограничения в изолированных визуальных веб-частей» в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Визуальные веб-части в изолированном решении возникнуть ошибка, «запрос на выполнение изолированного кода был отклонен, поскольку узел службы изолированного кода был слишком занят, чтобы обработать запрос.» Дополнительные сведения об этой ошибке см. в этой публикации [блог команды разработчиков SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Отладка JavaScript на стороне сервера не поддерживается в Visual Studio, но поддерживается Отладка JavaScript на стороне клиента.  
  
     Несмотря на то, что встроенный JavaScript можно добавить в файл разметки на стороне сервера, отладка не поддерживается для точек останова, добавляемым в разметку. Отладка JavaScript, ссылку на внешний файл JavaScript, в файле разметки и установите точки останова в файле JavaScript.  
  
-   Отладка встроенного [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] кода должно быть выполнено в файле сформированного кода, а не в файле разметки.  
  
-   Визуальные веб-части не поддерживают использование `<@ Assembly Src=` директивы.  
  
-   Веб-элементы управления, а также некоторые SharePoint [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] элементы управления не поддерживаются в изолированной среде SharePoint. Если используются неподдерживаемые элементы управления визуальной веб-части в изолированном решении, ошибки, отображается «Имя типа или пространства имен 'Theme' не существует в пространстве имен «Microsoft.SharePoint.WebControls»».  
  
 Дополнительные сведения об изолированных решениях см. в разделе [различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Создавать старого стиля SharePoint веб-части
 Шаблоны в Visual Studio можно использовать для создания пользовательских [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] веб-частей для SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] веб-частей построены на основе [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] инфраструктура веб-части и представляют собой рекомендуемые типы для новых проектов.  
  
 В очень редких случаях может потребоваться создать веб-части с помощью старого стиля SharePoint веб-части. Visual Studio можно использовать для создания этих типов веб-частей, но Visual Studio не предоставляет шаблоны, специально предназначенных для их создания.  
  
 Дополнительные сведения о когда может потребоваться создать старого стиля SharePoint веб-частей см. в разделе [уместно в Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Дополнительные сведения о создании веб-части с помощью старого стиля SharePoint веб-частей см. в разделе [Пошаговое руководство, Создание базовых веб-части SharePoint](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>См. также
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Показано, как создать веб-частей для SharePoint страницы.|  
|[Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Показано, как создать веб-частей для SharePoint с помощью визуального конструктора.|  
|[Практическое руководство. Создание пользовательского элемента управления для страницы приложения или веб-части SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Демонстрируется создание пользовательских, многократно используемых элементов управления, которые можно размещать на страницах приложений и веб-частей, которые выполняются в SharePoint.|  
|[Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Инструкции по разработке веб-части для SharePoint.|  
|[Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Инструкции по разработке веб-части для SharePoint путем перетаскивания элементов управления в рабочую область конструирования visual.|  
|[Пошаговое руководство. Создание веб-части Silverlight, которая отображает данные OData для SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Инструкции по разработке веб-части для SharePoint, где размещается приложение Silverlight и отображает данные из списков SharePoint.|  
  