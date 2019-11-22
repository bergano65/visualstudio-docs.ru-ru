---
title: Analyze and model your architecture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297945"
---
# <a name="analyze-and-model-your-architecture"></a>Анализ и моделирование архитектуры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы приложение соответствовало требованиям пользователей, используйте для его проектирования и моделирования инструменты моделирования и разработки архитектуры Visual Studio. Visual Studio поможет вам визуализировать структуру, поведение и отношения кода и разобраться в имеющемся программном коде.

 Программа позволяет создавать модели с разным уровнем детализации на протяжении всего жизненного цикла приложения. Отслеживайте требования, задачи, тестовые случаи, ошибки или другие типы работ, сопряженные с вашими моделями, связывая элементы модели с рабочими элементами Team Foundation Server и планом разработки. See [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>Целевой тип

|||
|-|-|
|**Визуализация кода**<br /><br /> -   See the code's organization and relationships by creating code maps. Визуализация зависимостей между сборками, пространствами имен, классами, методами и т. д.<br />-   See the class structure and members for a specific project by creating class diagrams from code.<br />-   Find conflicts between your code and its design by creating layer diagrams to validate code.<br /><br /> **Примечание**. В этой версии Visual Studio термин *карта кода* используется вместо *графа зависимостей*. Обычно, если термин *граф* используется отдельно, он обозначает направленный граф или схему (либо документ) DGML. Карты кода представляют собой особый тип схемы DGML.|-   [Визуализация кода](../modeling/visualize-code.md)<br />-   [Working with Classes and Other Types (Class Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Understand your code dependencies through visualization (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Visualize the impact of a change (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**Описание и сообщение требований пользователей**<br /><br /> -   Clarify user stories, business rules, and other requirements and help ensure their consistency by drawing UML diagrams such as use case, activity, and class diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**Определение архитектуры**<br /><br /> -   Model the large-scale structure of your software system and the design patterns by drawing UML component, class, and sequence diagrams.<br />-   Define and enforce constraints on dependencies between the components of your code by creating layer diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Проверка системы на соответствие требованиям и намеченной структуре**<br /><br /> -   Define acceptance tests or system tests based on the requirements models. Это позволяет создать прочные отношения между тестами и требованиями пользователей и легко обновлять систему при изменении требований.<br />-   Validate code dependencies with layer diagrams that describe the intended architecture and prevent changes that might conflict with the design.|-   [Validate your system during development](../modeling/validate-your-system-during-development.md)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Совместное использование моделей, схем и карт кода с помощью системы управления версиями Team Foundation**<br /><br /> -   Put code maps, modeling projects, UML diagrams, and layer diagrams under Team Foundation version control so you can share them.|Если в системе управления версиями Team Foundation с этими элементами работают несколько пользователей, соблюдайте приведенные здесь рекомендации. Это позволит избежать проблем с управлением версиями.<br /><br /> -   [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Создание или настройка частей приложения на основе UML или предметно-ориентированных языков**<br /><br /> -   Make your design more responsive to requirements changes and easily variable across a product line.|-   [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md)|
|**Настройка моделей и схем**<br /><br /> -   Adapt models to how your project uses them by defining additional properties for UML elements, validation constraints to make sure that your models conform to your business rules, and additional menu commands and toolbox items.<br />-   Create your own domain-specific languages.|-   [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Создание текстов с помощью шаблонов T4**<br /><br /> -   Use text blocks and control logic inside templates to generate text-based files.|-   [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Типы моделей и их применение

|**Тип модели и типичные способы применения**|
|-------------------------------------|
|**Карты кода**<br /><br /> Карты кода помогают увидеть структуру кода и имеющиеся в нем отношения.<br /><br /> Типичные способы применения:<br /><br /> -   Examine program code so you can better understand its structure and its dependencies, how to update it, and estimate the cost of proposed changes.<br /><br /> Пример<br /><br /> -   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Layer diagram**<br /><br /> Схемы слоев позволяют определить структуру приложения как набор слоев или блоков с явно заданными зависимостями. Для выявления конфликтов между зависимостями в коде и зависимостями, описанными в схеме слоев, можно выполнить проверку.<br /><br /> Типичные способы применения:<br /><br /> -   Stabilize the structure of the application through numerous changes over its life.<br />-   Discover unintentional dependency conflicts before checking in changes to the code.<br /><br /> Пример<br /><br /> -   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**UML model**<br /><br /> Модель UML включает несколько представлений, в том числе схемы классов, компонентов, вариантов использования, деятельности и последовательностей. UML можно настроить с учетом требований вашего домена приложения. Например, можно прикрепить к элементам модели теги, дополнительную информацию и ограничения. Кроме того, можно определить инструменты для работы с моделями. See [Create models for your app](../modeling/create-models-for-your-app.md).<br /><br /> Типичные способы применения:<br /><br /> -   Describe requirements and design. UML можно быстро применить к разработке любого приложения. See [Use models in your development process](../modeling/use-models-in-your-development-process.md).<br />-   Generate or configure tests or parts of an application. Для настройки нотации и разработки шаблонов создания или настраиваемых приложений требуются определенные действия. See [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md).<br />-   For general description and for code generation or configuration in smaller projects.|
|**Предметно-ориентированный язык**<br /><br /> Предметно-ориентированный язык представляет собой нотацию, разработанную для определенной цели. В Visual Studio обычно используется графическая нотация.<br /><br /> Типичные способы применения:<br /><br /> -   Generate or configure parts of the application. Разработка нотации и инструментов требует усилий. Результат может лучше соответствовать вашему домену, чем настройка языка UML.<br />-   For large projects or in product lines where the investment in developing the DSL and its tools is returned by its use in more than one project.<br /><br /> Пример<br /><br /> -   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Где можно получить дополнительные сведения?

|||
|-|-|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>См. также раздел

- [What's new for modeling in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps и управление жизненным циклом приложений](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
