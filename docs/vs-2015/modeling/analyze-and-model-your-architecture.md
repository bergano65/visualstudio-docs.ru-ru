---
title: Анализ и моделирование архитектуры | Документация Майкрософт
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
ms.openlocfilehash: 1a505cd9fd40a47c58135506cf7e022409e9b77e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852063"
---
# <a name="analyze-and-model-your-architecture"></a>Анализ и моделирование архитектуры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы приложение соответствовало требованиям пользователей, используйте для его проектирования и моделирования инструменты моделирования и разработки архитектуры Visual Studio. Visual Studio поможет вам визуализировать структуру, поведение и отношения кода и разобраться в имеющемся программном коде.

 Программа позволяет создавать модели с разным уровнем детализации на протяжении всего жизненного цикла приложения. Отслеживайте требования, задачи, тестовые случаи, ошибки или другие типы работ, сопряженные с вашими моделями, связывая элементы модели с рабочими элементами Team Foundation Server и планом разработки. См. раздел [сценарий. изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>Куда

|||
|-|-|
|**Визуализация кода**<br /><br /> — Просмотрите организацию кода и связи, создав карты кода. Визуализация зависимостей между сборками, пространствами имен, классами, методами и т. д.<br />— См. структуру классов и элементы для конкретного проекта путем создания схем классов на основе кода.<br />— Поиск конфликтов между кодом и его конструкцией путем создания схем слоев для проверки кода.<br /><br /> **Примечание**. В этой версии Visual Studio термин *карта кода* используется вместо *графа зависимостей*. Обычно, если термин *граф* используется отдельно, он обозначает направленный граф или схему (либо документ) DGML. Карты кода представляют собой особый тип схемы DGML.|-   [Визуализация кода](../modeling/visualize-code.md)<br />-   [работе с классами и другими типами (конструктор классов)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [видео: Общие сведения о зависимостях кода с помощью визуализации (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   [видео: Визуализация влияния изменения (канал 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**Описание и сообщение требований пользователей**<br /><br /> — Уточнение пользовательских историй, бизнес-правил и других требований и обеспечение их согласованности путем рисования схем UML, таких как примеры использования, действия и схемы классов.|-   [создания моделей для приложения](../modeling/create-models-for-your-app.md)<br />[требования к пользователям модели](../modeling/model-user-requirements.md) -   <br />-   [видео: улучшение архитектуры за счет моделирования (канал 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**Определение архитектуры**<br /><br /> — Моделирование крупномасштабной структуры программной системы и шаблонов проектирования путем рисования схем компонентов UML, классов и последовательностей.<br />— Определение и принудительное применение ограничений для зависимостей между компонентами кода путем создания схем слоев.|-   [создания моделей для приложения](../modeling/create-models-for-your-app.md)<br />-   [модель архитектуры приложения](../modeling/model-your-app-s-architecture.md)<br />-   [видео: улучшение архитектуры за счет моделирования (канал 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [видео: использование схем слоев для проектирования и проверки архитектуры (канал 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Проверка системы на соответствие требованиям и намеченной структуре**<br /><br /> — Определение приемочных тестов или системных тестов на основе моделей требований. Это позволяет создать прочные отношения между тестами и требованиями пользователей и легко обновлять систему при изменении требований.<br />— Проверка зависимостей кода с помощью схем слоев, описывающих предполагаемую архитектуру и предотвращающих изменения, которые могут конфликтовать со структурой.|-   [проверить систему во время разработки](../modeling/validate-your-system-during-development.md)<br />-   [видео: использование схем слоев для проектирования и проверки архитектуры (канал 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Совместное использование моделей, схем и карт кода с помощью системы управления версиями Team Foundation**<br /><br /> — Размещение карт кода, проектов моделирования, схем UML и схем слоев в системе управления версиями Team Foundation, чтобы вы могли поделиться ими.|Если в системе управления версиями Team Foundation с этими элементами работают несколько пользователей, соблюдайте приведенные здесь рекомендации. Это позволит избежать проблем с управлением версиями.<br /><br /> -   [Управление моделями и диаграммами в системе управления версиями](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Создание или настройка частей приложения на основе UML или предметно-ориентированных языков**<br /><br /> — Повышение скорости реагирования проекта на изменения требований и их простоту в линии продукта.|-   [создать и настроить приложение на основе моделей](../modeling/generate-and-configure-your-app-from-models.md)|
|**Настройка моделей и схем**<br /><br /> -Адаптация моделей в соответствии с их использованием в проекте путем определения дополнительных свойств элементов UML, ограничений проверки, чтобы гарантировать соответствие моделей бизнес-правилам, а дополнительные команды меню и элементы панели элементов.<br />— Создайте собственные языки для конкретных доменов.|-   [расширения моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)<br />[пакет SDK для моделирования -   для Visual Studio — языки, относящиеся к домену](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Создание текстов с помощью шаблонов T4**<br /><br /> — Использование текстовых блоков и логики элементов управления внутри шаблонов для создания текстовых файлов.|-   [создания кода и текстовых шаблонов T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Типы моделей и их применение

|**Тип модели и типичные способы применения**|
|-------------------------------------|
|**Карты кода**<br /><br /> Карты кода помогают увидеть структуру кода и имеющиеся в нем отношения.<br /><br /> Типичные способы применения:<br /><br /> — Изучите программный код, чтобы лучше понять его структуру и зависимости, как обновить ее и оценить стоимость предлагаемых изменений.<br /><br /> См.:<br /><br /> -   [сопоставлять зависимости в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [использования карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Схема слоев**<br /><br /> Схемы слоев позволяют определить структуру приложения как набор слоев или блоков с явно заданными зависимостями. Для выявления конфликтов между зависимостями в коде и зависимостями, описанными в схеме слоев, можно выполнить проверку.<br /><br /> Типичные способы применения:<br /><br /> — Стабилизация структуры приложения за счет многочисленных изменений в течение его жизненного цикла.<br />— Обнаружение непреднамеренного конфликта зависимостей перед возвратом изменений в код.<br /><br /> См.:<br /><br /> -   [создания схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)<br />-   [проверки кода с помощью схем слоев](../modeling/validate-code-with-layer-diagrams.md)|
|**Модель UML**<br /><br /> Модель UML включает несколько представлений, в том числе схемы классов, компонентов, вариантов использования, деятельности и последовательностей. UML можно настроить с учетом требований вашего домена приложения. Например, можно прикрепить к элементам модели теги, дополнительную информацию и ограничения. Кроме того, можно определить инструменты для работы с моделями. См. раздел [Создание моделей для приложения](../modeling/create-models-for-your-app.md).<br /><br /> Типичные способы применения:<br /><br /> — Опишите требования и структуру. UML можно быстро применить к разработке любого приложения. См. раздел [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md).<br />— Создание или настройка тестов или частей приложения. Для настройки нотации и разработки шаблонов создания или настраиваемых приложений требуются определенные действия. См. статью [Создание и настройка приложения на основе моделей](../modeling/generate-and-configure-your-app-from-models.md).<br />— Для общего описания и для создания или настройки кода в небольших проектах.|
|**Предметно-ориентированный язык**<br /><br /> Предметно-ориентированный язык представляет собой нотацию, разработанную для определенной цели. В Visual Studio обычно используется графическая нотация.<br /><br /> Типичные способы применения:<br /><br /> — Создание или настройка частей приложения. Разработка нотации и инструментов требует усилий. Результат может лучше соответствовать вашему домену, чем настройка языка UML.<br />— Для больших проектов или в строках продукта, в которых инвестиции в разработку DSL и его средства возвращаются в нескольких проектах.<br /><br /> См.:<br /><br /> [пакет SDK для моделирования -   для Visual Studio — языки, относящиеся к домену](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Где можно получить дополнительные сведения?

|||
|-|-|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>См. также раздел

- [Новые возможности моделирования в Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps и управление жизненным циклом приложений](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
