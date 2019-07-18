---
title: Создание веб-частей для SharePoint | Документация Майкрософт
ms.date: 02/02/2017
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
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1105e6c68e1ec9083fd790ad8a38b09870345af2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580956"
---
# <a name="create-web-parts-for-sharepoint"></a>Создание веб-частей для SharePoint
  С помощью веб-частей, можно изменить содержимое, внешний вид и поведение страниц сайта SharePoint с помощью браузера. Веб-части, серверных элементов управления, выполняемые внутри страницы: они являются стандартными блоками страниц, отображаемых на сайте SharePoint. См. в разделе [стандартный блок: Веб-части](http://go.microsoft.com/fwlink/?LinkID=182097).

 Можно создать и отладка веб-частей на сайте SharePoint с помощью шаблонов из Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Создание веб-части в Visual Studio
 Создать веб-часть, добавив **веб-часть** элемента в любой проект SharePoint. Можно использовать **веб-часть** элемента в изолированном решении или решении фермы.

 Если вы хотите создать веб-часть визуально с помощью конструктора, создайте **визуальной веб-части** проекта или добавить **визуальной веб-части** элемент в любой проект SharePoint. Можно использовать **визуальной веб-части** элемент только решения фермы.

### <a name="web-part-item"></a>Элемент веб-части
 Объект **веб-часть** содержит файлы, которые можно использовать для разработки веб-части для сайта SharePoint. При добавлении **веб-часть** товар, Visual Studio создает папку в проекте и добавляет в нее несколько файлов. В следующей таблице описаны каждого файла.

|Файл|Описание|
|----------|-----------------|
|*Elements.XML*|Содержит сведения, используемые файлом определения компонента в проекте используется для развертывания веб-части.|
|файл .webpart|Предоставляет сведения, необходимые для отображения веб-части в веб-частей SharePoint.|
|Файл кода|Содержит методы, добавляющие элементы управления в веб-часть и создающие пользовательское содержимое внутри веб-части.|

 Дополнительные сведения см. в разделе [Как Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Элемент Visual веб-части
 Визуальная веб-часть является веб-части, созданной с помощью конструктора Visual Web Developer в Visual Studio. Визуальная веб-часть функционирует так же, как любой другой веб-части. Чтобы добавить элементы управления, такие как кнопки и текстовые поля, для веб-части, добавьте код в XML-файл. Тем не менее, добавление элементов управления для визуальной веб-части, перетащив или скопировав их на веб-части из Visual Studio **элементов**. Затем конструктор создает требуемый код в XML-файле. См. практическое руководство по [ Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Элементы управления SharePoint
 Visual Studio предоставляет некоторые элементы управления для создания страницы SharePoint, например страницы приложения. Эти элементы управления отображаются в **элементов** под **элементы управления SharePoint**. Функциональные возможности для этих элементов управления является производным от [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) пространство имен, которое содержит серверные элементы управления ASP.NET, которые используются на страницах сайта и списка SharePoint.

|Имя элемента|Описание|
|------------------|-----------------|
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Вставляет меню ASP. Дополнительные сведения см. в разделе [Обзор элемента управления меню](http://go.microsoft.com/fwlink/?LinkId=235316).|
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Вставляет **ССЫЛКУ** элемент в коллекцию *.aspx* странице и применяет один или несколько внешних таблиц стилей определяется **CssRegistration**.|
|[Элемент управления DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Вставляет элемент управления DateTime в *.aspx* страницы.|
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Вставляет проверку безопасности в *.aspx* страницы|
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Возвращает свойство указанного списка.|
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Возвращает глобальное свойство текущего веб-сайта.|
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Вставляет ссылку на RSS-канал *.aspx* страницы.|
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Предоставляет свойства и методы для регистрации ресурсы, такие как скрипты на странице, таким образом, чтобы их можно было задать при отображении страницы.|
|[Тема](http://go.microsoft.com/fwlink/?LinkId=235314)|Применяет тему к *.aspx* страницы.|

## <a name="debug-a-web-part"></a>Отладка веб-части
 Можно отлаживать проект SharePoint, который содержит веб-часть, так же, как отладка других проектов Visual Studio. При запуске отладчика Visual Studio, Visual Studio открывает сайт SharePoint.

 Чтобы начать отладку кода, добавьте веб-часть на страницу веб-частей в SharePoint.

 Дополнительные сведения об отладке проектов SharePoint см. в разделе [решений SharePoint, устранение неполадок](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Visual web часть ограничения
 Начиная с Visual Studio, можно добавить визуальные веб-части в изолированные решения SharePoint и решениями для фермы. Однако визуальные веб-части имеют следующие ограничения:

- Визуальные веб-части не поддерживает подстановочных параметров. Дополнительные сведения см. в разделе [подстановочных параметров](../sharepoint/replaceable-parameters.md).

- Пользовательские элементы управления или визуальные веб-части невозможно перетащить и удалить или скопировать на визуальные веб-части. Это действие приводит к ошибке сборки.

- Визуальные веб-части непосредственно не поддерживают токены сервера SharePoint как $SPUrl. Дополнительные сведения см. в разделе «Токена ограничения в изолированных визуальных веб-частей» в разделе [решений SharePoint, устранение неполадок](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Визуальные веб-части в изолированном решении иногда получают ошибку, «запрос выполнения изолированного кода был отклонен, поскольку основная служба изолированного кода была слишком занят, чтобы обработать запрос.» Дополнительные сведения об этой ошибке см. в записи [блога команды разработчиков SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).

- Отладка JavaScript на стороне сервера не поддерживается в Visual Studio, но поддерживается Отладка JavaScript на стороне клиента.

   Несмотря на то, что встроенный JavaScript можно добавить в файл разметки на стороне сервера, отладка не поддерживается для точек останова, добавленных в разметку. Для отладки JavaScript, ссылаться на внешний файл JavaScript в файле разметки и затем установите точки останова в файле JavaScript.

- Отладка подставляемого [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] кода должна быть выполнена в файле сформированного кода, а не в файле разметки.

- Визуальные веб-части не поддерживают использование `<@ Assembly Src=` директива.

- SharePoint веб-элементы управления и некоторые [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] элементы управления не поддерживаются в среде изолированных решений SharePoint. Если неподдерживаемые элементы управления используются в визуальной веб-части в изолированном решении, ошибки, отображается «Тип или пространство имен имя «Theme» не существует в пространстве имен «Microsoft.SharePoint.WebControls»».

  Дополнительные сведения об изолированных решениях см. в разделе [различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Создание старого стиля SharePoint веб-частей
 Можно использовать шаблоны в Visual Studio для создания пользовательских [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] веб-части для SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] веб-частей строятся на основе [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] инфраструктура веб-части и рекомендуемый тип для новых проектов.

 В очень редких случаях может потребоваться создание веб-части с помощью старого стиля SharePoint веб-части. Visual Studio можно использовать для создания этих типов веб-частей, но Visual Studio не предусмотрено шаблонов, которые предназначены специально для их создания.

 Дополнительные сведения о когда может потребоваться создать старого стиля SharePoint веб-части, см. в разделе [инфраструктура веб-частей в службах Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Дополнительные сведения о способах создания веб-части с помощью SharePoint веб-части старого стиля см. в разделе [пошаговым руководством по созданию базовых веб-частей SharePoint](http://go.microsoft.com/fwlink/?LinkId=169288).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Показано, как создать веб-частей для страниц SharePoint.|
|[Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Показано, как создать веб-частей для SharePoint с помощью визуальную область конструктора.|
|[Практическое руководство. Создать пользовательский элемент управления для части страницы или веб-приложения SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Показано, как создать пользовательские элементы управления, которые могут быть использованы на страницах приложений и веб-частей, которые выполняются в SharePoint.|
|[Пошаговое руководство: Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Инструкции по разработке веб-части для SharePoint.|
|[Пошаговое руководство: Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Описываются способы разработки веб-части для SharePoint путем перетаскивания элементов управления визуальную область конструктора.|
|[Пошаговое руководство: Создание веб-части Silverlight, отображающей данные OData для SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Инструкции по разработке веб-части для SharePoint, которое размещается приложение Silverlight и отображает данные из списков SharePoint.|
