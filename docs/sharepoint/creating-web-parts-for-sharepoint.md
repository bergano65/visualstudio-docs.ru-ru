---
title: Создание веб-части для SharePoint | Документация Майкрософт
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
ms.openlocfilehash: 82e0d860f21f0fe2744c8c05c4ebeb3590be68fc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984478"
---
# <a name="create-web-parts-for-sharepoint"></a>Создание веб-частей для SharePoint
  С помощью веб-частей можно изменять содержимое, внешний вид и поведение страниц сайта SharePoint с помощью браузера. Веб-части — это элементы управления на стороне сервера, которые выполняются на странице веб-частей: они являются стандартными блоками страниц, которые отображаются на сайте SharePoint. См. раздел [стандартный блок: веб-части](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Вы можете создавать и отлаживать веб-части на сайте SharePoint с помощью шаблонов из Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Создание веб-части в Visual Studio
 Создайте веб-часть, добавив элемент **веб-части** в любой проект SharePoint. Элемент **веб-части** можно использовать в изолированном решении или в решении фермы.

 Если вы хотите визуально разработать веб-часть с помощью конструктора, создайте проект **визуальной веб-части** или добавьте элемент **визуальной веб-части** в любой проект SharePoint. Элемент **визуальной веб-части** можно использовать только в решении фермы.

### <a name="web-part-item"></a>Элемент веб-части
 Элемент **веб-части** предоставляет файлы, которые можно использовать для разработки веб-части для сайта SharePoint. При добавлении элемента **веб-части** Visual Studio создает в проекте папку, а затем добавляет в нее несколько файлов. В следующей таблице описывается каждый файл.

|Файл|Описание|
|----------|-----------------|
|*Elements. XML*|Содержит сведения, которые файл определения компонента в проекте использует для развертывания веб-части.|
|файл. WebPart|Предоставляет сведения, необходимые SharePoint для показа веб-части в галерее веб-частей.|
|Файл кода|Содержит методы, добавляющие элементы управления в веб-часть и создающие пользовательское содержимое в веб-части.|

 Дополнительные сведения см. [в разделе инструкции. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Элемент визуальной веб-части
 Визуальная веб-часть — это веб-часть, созданная с помощью конструктора Visual Web Developer в Visual Studio. Визуальная веб-часть функционирует так же, как и любая другая веб-часть. Чтобы добавить элементы управления, такие как кнопки и текстовые поля, в веб-часть, добавьте код в XML-файл. Однако элементы управления добавляются в визуальную веб-часть путем их перетаскивания или копирования в веб-часть из **панели элементов**Visual Studio. Затем конструктор создает необходимый код в XML-файле. См. раздел [как создать веб-часть SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Элементы управления SharePoint
 Visual Studio предоставляет некоторые элементы управления для создания страниц SharePoint, таких как страницы приложений. Эти элементы управления отображаются в области **элементов** в разделе **элементы управления SharePoint**. Функциональность этих элементов управления является производной от пространства имен [Microsoft. SharePoint.](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) ASP.NET, которое содержит серверные элементы управления, используемые на страницах сайтов и списков SharePoint.

|Имя элемента|Описание|
|------------------|-----------------|
|[аспмену](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Вставляет меню ASP. Дополнительные сведения см. в разделе [Общие сведения об элементе управления Menu](/previous-versions/ecs0x9w5(v=vs.140)).|
|[ксслинк](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Вставляет элемент **ссылки** на *ASPX* -страницу и применяет одну или несколько внешних таблиц стилей, определенных **кссрегистратион**.|
|[датетимеконтрол](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Вставляет элемент управления DateTime на страницу *ASPX* .|
|[формдижест](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Вставка проверки безопасности на *ASPX* -страницу|
|[листпроперти](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Возвращает свойство указанного списка.|
|[прожектпроперти](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Возвращает глобальное свойство текущего веб-сайта.|
|[рсслинк](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Вставляет ссылку на RSS-канал на страницу *. aspx* .|
|[скриптлинк](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Предоставляет свойства и методы для регистрации ресурсов, таких как скрипты, на странице, чтобы их можно было запрашивать при подготовке страницы к просмотру.|
|[Тема](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Применяет тему к странице *. aspx* .|

## <a name="debug-a-web-part"></a>Отладка веб-части
 Можно выполнить отладку проекта SharePoint, содержащего веб-часть, так же, как отладка других проектов Visual Studio. При запуске отладчика Visual Studio Visual Studio открывает сайт SharePoint.

 Чтобы начать отладку кода, добавьте веб-часть на страницу веб-частей в SharePoint.

 Дополнительные сведения об отладке проектов SharePoint см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Ограничения визуальных веб-частей
 Начиная с Visual Studio, можно добавлять визуальные веб-части в изолированные решения SharePoint и решения фермы. Однако визуальные веб-части имеют следующие ограничения.

- Визуальные веб-части не поддерживают заменяемые параметры. Дополнительные сведения см. в разделе [заменяемые параметры](../sharepoint/replaceable-parameters.md).

- Пользовательские элементы управления или визуальные веб-части нельзя перетаскивать и удалять или копировать в визуальные веб-части. Это действие вызывает ошибку сборки.

- Визуальные веб-части напрямую не поддерживают маркеры сервера SharePoint, такие как $SPUrl. Дополнительные сведения см. в разделе "ограничения токенов в изолированных визуальных веб-части" статьи [Устранение неполадок в решениях SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Визуальные веб-части в изолированном решении иногда возникнет ошибка "запрос на выполнение изолированного кода был отклонен, так как служба узла изолированного кода слишком занята для обработки запроса". Дополнительные сведения об этой ошибке см. в этой записи в [блоге группы разработчиков SharePoint](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157).

- Отладка JavaScript на стороне сервера не поддерживается в Visual Studio, но поддерживается отладка JavaScript на стороне клиента.

   Хотя встроенный код JavaScript можно добавить в файл разметки на стороне сервера, отладка не поддерживается для точек останова, добавленных в разметку. Чтобы выполнить отладку JavaScript, сослаться на внешний файл JavaScript в файле разметки, а затем задать точки останова в файле JavaScript.

- Отладка встроенного [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] кода должна выполняться в созданном файле кода, а не в файле разметки.

- Визуальные веб-части не поддерживают использование директивы `<@ Assembly Src=`.

- Веб-элементы управления SharePoint и некоторые [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] элементы управления не поддерживаются в изолированной среде SharePoint. Если неподдерживаемые элементы управления используются в визуальной веб-части в изолированном решении, то ошибка "тип или имя пространства имен" Theme "не существует в пространстве имен" Microsoft. SharePoint. веб-элементы управления "".

  Дополнительные сведения об изолированных решениях см. в разделе [различия между изолированными и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Создание веб-частей на основе SharePoint прежних версий
 Шаблоны в Visual Studio можно использовать для создания пользовательских веб-частей [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] для SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] веб-части построены на основе [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] инфраструктуры веб-частей и являются рекомендуемым типом для новых проектов.

 В редких случаях может потребоваться создать веб-часть с помощью старой веб-части на основе SharePoint. Вы можете использовать Visual Studio для создания таких веб-частей, но Visual Studio не предоставляет шаблоны, специально предназначенные для их создания.

 Дополнительные сведения о том, когда может потребоваться создать веб-часть на основе SharePoint прежних версий, см. [в разделе Инфраструктура веб-частей в службах Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Дополнительные сведения о создании веб-части с помощью устаревшей веб-части на основе SharePoint см. в разделе [Пошаговое руководство по созданию базовой веб-части SharePoint](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Как создать веб-часть SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Показывает, как создавать веб-части для страниц SharePoint.|
|[Инструкции. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Показывает, как создавать веб-части для SharePoint с помощью визуальной рабочей области конструирования.|
|[Как создать пользовательский элемент управления для страницы приложения SharePoint или веб-части](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Показывает, как создавать настраиваемые, многократно используемые элементы управления, которые могут использоваться страницами приложений и веб-частями, выполняемыми в SharePoint.|
|[Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Описывает создание веб-части для SharePoint.|
|[Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Описывает создание веб-части для SharePoint путем перетаскивания элементов управления в рабочую область визуального конструирования.|
|[Пошаговое руководство. Создание веб-части Silverlight, которая отображает OData для SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Описывает создание веб-части для SharePoint, в которой размещается приложение Silverlight, и отображение данных из списков SharePoint.|
