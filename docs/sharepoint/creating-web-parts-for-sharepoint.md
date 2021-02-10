---
title: Создание веб-частей для SharePoint | Документация Майкрософт
description: Создание веб-частей для SharePoint. С помощью веб-частей можно изменять содержимое, внешний вид и реакцию на события страниц сайта SharePoint, используя браузер.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae28ab44b12c979f3c405bd7d853d7a2d196aae4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948938"
---
# <a name="create-web-parts-for-sharepoint"></a>Создание веб-частей для SharePoint
  С помощью веб-частей можно изменять содержимое, внешний вид и реакцию на события страниц сайта SharePoint, используя браузер. Веб-части — это элементы управления на стороне сервера, которые выполняются на странице веб-частей. Они являются стандартными блоками страниц, которые отображаются на сайте SharePoint. См. раздел [Стандартный блок. Веб-части](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Вы можете создавать и отлаживать веб-части на сайте SharePoint с помощью шаблонов из Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Создание веб-части в Visual Studio
 Чтобы создать веб-часть, добавьте элемент **Web Part** (Веб-часть) в любой проект SharePoint. Элемент **Веб-часть** можно использовать в изолированном решении или в решении фермы.

 Если вы хотите визуально разработать веб-часть с помощью конструктора, создайте проект **визуальной веб-части** или добавьте элемент **Visual Web Part** (Визуальная веб-часть) в любой проект SharePoint. Элемент **Визуальная веб-часть** можно использовать только в решении фермы.

### <a name="web-part-item"></a>Элемент "Веб-часть"
 Элемент **Веб-часть** содержит файлы, используемые для разработки веб-частей для сайтов SharePoint. При добавлении элемента **Веб-часть** Visual Studio создает в проекте папку, а затем добавляет в нее несколько файлов. Эти файлы описываются в следующей таблице.

|Файл|Описание|
|----------|-----------------|
|*Elements.xml*|Содержит сведения, которые файл определения компонента в проекте использует для развертывания веб-части.|
|WEBPART-файл|Содержит сведения, необходимые SharePoint для отображения этой веб-части в коллекции веб-частей.|
|Файл кода|Содержит методы, добавляющие элементы управления в веб-часть и создающие пользовательское содержимое в веб-части.|

 Дополнительные сведения см. в разделе [Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Элемент "Визуальная веб-часть"
 Визуальная веб-часть — это веб-часть, созданная с помощью конструктора Visual Web Developer в Visual Studio. Визуальная веб-часть функционирует так же, как и любая другая веб-часть. Чтобы добавить в веб-часть элементы управления, такие как кнопки и текстовые поля, добавьте код в XML-файл. Однако чтобы добавить элементы управления в визуальную веб-часть, их необходимо перетащить или скопировать в веб-часть из **панели элементов**. Затем конструктор создает необходимый код в XML-файле. См. практическое руководство по [ созданию веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Элементы управления SharePoint
 Visual Studio предоставляет несколько элементов управления для создания страниц SharePoint, например страниц приложений. Эти элементы управления отображаются в **панели элементов** в разделе **Элементы управления SharePoint**. Функциональные возможности этих элементов управления наследуются из пространства имен [Microsoft.SharePoint.SharePoint.WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)), которое содержит элементы управления ASP.NET, используемые на страницах сайта и списка SharePoint.

|Название элемента управления|Описание|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Вставляет меню ASP. Дополнительные сведения см. в разделе [Обзор элементов управления меню](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Вставляет элемент **LINK** на страницу *ASPX* и применяет одну или несколько внешних таблиц стилей, определенных параметром **CssRegistration**.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Вставляет элемент управления DateTime на страницу *ASPX*.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Вставляет проверку безопасности на страницу *ASPX*.|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Возвращает свойство указанного списка.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Возвращает глобальное свойство текущего веб-сайта.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Вставляет ссылку на RSS-канал на страницу *ASPX*.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Предоставляет свойства и методы для регистрации на странице ресурсов, таких как скрипты, чтобы их можно было запрашивать при подготовке страницы к просмотру.|
|[Тема](/previous-versions/office/sharepoint-server/ms460735(v=office.15)).|Применяет тему к странице *ASPX*.|

## <a name="debug-a-web-part"></a>Отладка веб-части
 Отладка проекта SharePoint, содержащего веб-часть, выполняется так же, как отладка других проектов Visual Studio. При запуске отладчика Visual Studio открывается сайт SharePoint.

 Чтобы начать отладку кода, добавьте веб-часть на страницу веб-частей в SharePoint.

 Дополнительные сведения об отладке проектов SharePoint см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Ограничения визуальной веб-части
 Начиная с Visual Studio вы можете добавлять визуальные веб-части в изолированные решения SharePoint и решения фермы. Однако визуальные веб-части имеют следующие ограничения.

- Визуальные веб-части не поддерживают заменяемые параметры. Дополнительные сведения см. в разделе [Заменяемые параметры](../sharepoint/replaceable-parameters.md).

- Пользовательские элементы управления или визуальные веб-части нельзя перетаскивать и удалять, а также копировать в визуальные веб-части. Это действие приводит к возникновению ошибки сборки.

- Визуальные веб-части напрямую не поддерживают токены сервера SharePoint, такие как $SPUrl. Дополнительные сведения см. в разделе "Ограничения токенов в изолированных визуальных веб-частях" статьи [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- В визуальных веб-частях в изолированном решении иногда возникает ошибка "Запрос на выполнение изолированного кода отклонен, так как служба узла изолированного кода слишком загружена для обработки запроса". Дополнительные сведения об этой ошибке см. в этой публикации в [блоге команды разработчиков SharePoint](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157).

- Отладка JavaScript на стороне сервера в Visual Studio не поддерживается, но поддерживается отладка JavaScript на стороне клиента.

   Хотя встроенный код JavaScript можно добавить в файл разметки на стороне сервера, отладка не поддерживается для точек останова, добавленных в разметку. Для отладки JavaScript сделайте ссылку на внешний файл JavaScript в файле разметки, а затем задайте точки останова в файле JavaScript.

- Отладка встроенного кода [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] должна выполняться в созданном файле кода, а не в файле разметки.

- Визуальные веб-части не поддерживают использование директивы `<@ Assembly Src=`.

- Веб-элементы управления SharePoint и некоторые элементы управления [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] не поддерживаются в изолированной среде SharePoint. При использовании неподдерживаемых элементов управления в визуальной веб-части в изолированном решении возникает ошибка "Тип или имя пространства имен Theme не существует в пространстве имен Microsoft.SharePoint.WebControls".

  Дополнительные сведения об изолированных решениях см. в разделах [Различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Создание веб-частей старого стиля на основе SharePoint
 Шаблоны в Visual Studio можно использовать, чтобы создать пользовательские веб-части [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] для SharePoint. Веб-части [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] основаны на инфраструктуре веб-частей [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] и являются рекомендуемыми типами для новых проектов.

 В редких случаях может потребоваться создать веб-часть с помощью веб-части старого стиля на основе SharePoint. Чтобы создать такие веб-части, можно использовать Visual Studio, но Visual Studio не предоставляет шаблоны, специально предназначенные для их создания.

 Дополнительные сведения о том, когда может потребоваться создать веб-часть старого стиля на основе SharePoint, см. в разделе [Инфраструктура веб-частей в Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Дополнительные сведения о создании веб-части с помощью веб-части старого стиля на основе SharePoint см. в разделе [Пошаговое руководство. Создание базовой веб-части SharePoint](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Показывается, как создавать веб-части для страниц SharePoint.|
|[Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Показывается, как создавать веб-части для SharePoint с помощью визуального конструктора.|
|[Практическое руководство. Создание пользовательского элемента управления для страницы приложения или веб-части SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Показывается, как создавать пользовательские элементы управления с возможностью многократного использования, которые можно размещать на страницах приложений и в веб-частях, работающих в SharePoint.|
|[Пошаговое руководство: создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Описывается разработка веб-части для SharePoint.|
|[Пошаговое руководство: создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Описывается создание веб-части для SharePoint путем перетаскивания элементов управления в область визуального проектирования.|
|[Пошаговое руководство: создание веб-части Silverlight, отображающей данные OData для SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Описывается разработка веб-части для SharePoint, которая размещает приложение Silverlight и отображает данные из списков SharePoint.|