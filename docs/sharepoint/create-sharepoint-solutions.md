---
title: Создание решений SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1e5be38d0d44912052466162abaaa496c608d27
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981294"
---
# <a name="create-sharepoint-solutions"></a>Создание решений SharePoint
  Приложения SharePoint можно создавать не только в SharePoint Designer, но и в Visual Studio. Visual Studio обеспечивает быструю разработку решений SharePoint с помощью таких компонентов, как средства расширенной отладки, IntelliSense, завершение операторов и шаблоны проектов. В Visual Studio также используются преимущества дополнительных средств и языков платформы .NET Framework. Проекты SharePoint можно разрабатывать с помощью Visual Basic или Visual C#, а приложения для проектов SharePoint можно разрабатывать с помощью JavaScript.

 Сведения о SharePoint 2013 и надстройках SharePoint см. в разделах [SharePoint 2013](https://products.office.com/previous-versions/microsoft-sharepoint-2013) и [Создание приложений для SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

> [!NOTE]
> Узнайте, как использовать новую [модель надстроек SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) для расширения возможностей пользователей SharePoint. Эти надстройки требуют очень мало ресурсов по сравнению с традиционными решениями SharePoint, и их можно создавать с помощью почти любой технологии веб-программирования, такой как HTML5, JavaScript, CSS3 и XML.

|||
|-|-|
|![Документация](../sharepoint/media/vs-icon-documentation.gif "Документация")|**Документация**<br /><br /> -   [Начало &#40;разработки SharePoint в Visual Studio&#41; ](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [разработки решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)<br />-   [локализации решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [сборки и отладки решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [пакет и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [расширения средств SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|
|![Документация](../sharepoint/media/vs-icon-documentation.gif "Документация")|**Рекомендуемые задачи**<br /><br /> -   [Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [. Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [. Создание модели BDC](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [. Создание пользовательского элемента управления для страницы приложения SharePoint или веб-части](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![Пошаговые руководства](../sharepoint/media/vs-icon-walkthroughs.gif "Пошаговые руководства")|**Пошаговые руководства**<br /><br /> -   [Пошаговые руководства по разработке для SharePoint](../sharepoint/sharepoint-development-walkthroughs.md)|
|![Примеры кода](../sharepoint/media/vs-icon-codesamples.gif "Примеры кода")|**Примеры кода**<br /><br /> -   [примеры разработки SharePoint](../sharepoint/sharepoint-development-samples.md)<br />-   [Загрузки разработчика SharePoint](/sharepoint/dev/)|
|![Предлагает](../sharepoint/media/vs-icon-training.gif "Обучение")|**Предлагает**<br /><br /> -   [Обучение разработке для SharePoint](/sharepoint/dev/)|
|![Форумы](../sharepoint/media/vs-icon-forums.gif "Форумы")|**Форумы**<br /><br /> -   [Разработка для SharePoint в Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment)<br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![Предлагает](../sharepoint/media/vs-icon-training.gif "Обучение")|**Блоги**<br /><br /> -   [Блог о разработке приложений SharePoint в Visual Studio](https://blogs.msdn.microsoft.com/vssharepointtoolsblog/)|
|![Инструкции Презентации](../sharepoint/media/vs-icon-howdoivideos.gif "Инструкции Презентации")|**Инструкции Презентации**<br /><br /> -   [Практические советы. Создание визуальных веб-частей для SharePoint 2010 в Visual Studio 2010](https://visualstudio.microsoft.com/)<br />-   [Практические советы. Создание типов контента для SharePoint 2010 в Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [Практические советы. Создание определений сайтов для SharePoint 2010 в Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [Практические советы. Создание модели подключения к бизнес-данным для SharePoint 2010 с помощью Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Видеоролики Channel 9](../sharepoint/media/vs-icon-channel9videos.gif "Видеоматериалы канала 9")|**Видеоролики Channel 9**<br /><br /> -   [Обзор разработки приложений SharePoint в Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010)<br />-   [Рекомендации по созданию веб-частей SharePoint 2010 с помощью Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010)<br />-   [Конструкторы пакетов и компонентов SharePoint в Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010)|
|![Центр разработчиков](../sharepoint/media/vs-icon-msdndevcenter.gif "Центр разработчика")|**Центры разработчиков**<br /><br /> -   [Центр по разработке в Visual Studio](https://visualstudio.microsoft.com/)<br />-   [Центр по разработке для SharePoint](/sharepoint/dev/)<br />-   [Центр по разработке для SharePoint Server](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [Центр по разработке для SharePoint Designer](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [Центр по разработке для ASP.NET](https://msdn.microsoft.com/aa336522.aspx)|
|![Предоставление отзывов](../sharepoint/media/vs-icon-feedback.gif "Обратная связь")|**Предоставление отзывов**<br /><br /> Предоставьте отзыв о Visual Studio:<br /><br /> -   [Microsoft Connect](/collaborate/connect-redirect)<br /><br /> Предоставьте отзыв о документации по Visual Studio:<br /><br /> -   **Упрощенный вид.** В начале каждого раздела можно щелкнуть ссылку **Оценить этот раздел** , чтобы перейти к концу раздела, где можно выбрать **Да** или **Нет** в ответ на вопрос **Была ли эта страница полезной?** Затем можно установить один или несколько флажков, отображаемые при выборе варианта **Нет**, ввести дополнительные сведения в текстовом поле или и то и другое. По завершении нажмите кнопку **Отправить** .<br />-   **Вид без сценариев.** В верхней части раздела выберите ссылку **отзыва** , чтобы оставить отзыв на форуме обратной связи TechNet и библиотеки выражений.<br />-   **Классический вид.** В верхней части раздела выберите ссылку **«Щелкните, чтобы оценить» и «Отправить отзыв»** для предоставления отзывов о разделе в группу по разработке документации.|
