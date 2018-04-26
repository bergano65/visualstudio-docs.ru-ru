---
title: Анализ и моделирование архитектуры
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a0547374087927e7fc2d3da89c3fe4f2a5c2b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="analyze-and-model-your-architecture"></a>Анализ и моделирование архитектуры
Убедитесь в том, что ваше приложение требованиям архитектуры с помощью архитектуры Visual Studio и инструментов для разработки и моделирования приложения моделирования.

* Visual Studio поможет вам визуализировать структуру, поведение и отношения кода и разобраться в имеющемся программном коде.

* Расскажите команды в потребность в этом соблюдаются архитектуры зависимости.

* Программа позволяет создавать модели с разным уровнем детализации на протяжении всего жизненного цикла приложения.

В разделе [сценарий: изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>Кому

|||
|-|-|
|**Визуализация кода**<br /><br /> — Здесь можно увидеть организации и отношений в коде путем создания карт кода. Визуализация зависимостей между сборками, пространствами имен, классами, методами и т. д.<br />— Здесь можно увидеть структуры и членов классов конкретного проекта путем создания схем классов из кода.<br />— Поиск конфликтов между кодом и его структурой путем создания схем зависимостей для проверки кода.|-   [Визуализация кода](../modeling/visualize-code.md)<br />-   [Работа с классами и другими типами (конструктор классов)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Видео: Выявление конструктора из кода с помощью карт кода Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Видео: Проверка архитектуры зависимостей в режиме реального времени](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Определение архитектуры**<br /><br /> -Определение и наложение ограничений на зависимости между компонентами кода путем создания схем зависимостей.|-   [Видео: Проверка архитектуры зависимостей с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Проверка системы на соответствие требованиям и намеченной структуре**<br /><br /> -Проверка зависимостей кода с помощью схем зависимостей, которые описывают предполагаемую архитектуру и предотвращают внесение изменений, которые могут конфликтовать с проектом.|-   [Видео: Проверка архитектуры зависимостей с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Совместное использование моделей, схем и карт кода с помощью системы управления версиями Team Foundation**<br /><br /> -Поместите карт кода, проектов и схем deoendency в системе управления версиями Team Foundation, вы можете использовать их.| |
|**Настройка моделей и схем**<br /><br /> -Создание собственных доменных языков.|-   [Пакет SDK для моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Создание текстов с помощью шаблонов T4**<br /><br /> -Используйте блоков текста и контроль логики внутри шаблонов для создания текстовых файлов.<br /> -Построение шаблона T4 с помощью MSBuild, которые включены в Visual Studio|-   [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)|

Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="types-of-models-and-their-uses"></a>Типы моделей и их применение

|**Тип модели и типичные способы применения**|
|-------------------------------------|
|**Карты кода**<br /><br /> Карты кода помогают увидеть структуру кода и имеющиеся в нем отношения.<br /><br /> Типичные способы применения:<br /><br /> -Изучите программный код, можно понять его структуру и зависимости, порядок обновления и расчетную стоимость реализации предлагаемых изменений.<br /><br /> Пример<br /><br /> -   [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Диаграмма зависимостей**<br /><br /> Схемы зависимостей позволяют определить структуру приложения как набор слоев или блоков с явно заданными зависимостями. Можно выполнить проверку для выявления конфликтов между зависимостями в коде и зависимостями, описанными в схеме зависимостей.<br /><br /> Типичные способы применения:<br /><br /> — Стабилизация структуры приложения путем внесения многочисленных изменений в течение его жизненного цикла.<br />— Выявление непредвиденных конфликтов зависимостей до возвращения изменений кода.<br /><br /> Пример<br /><br /> -   [Создание схемы зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Схемы зависимостей: Справочник](../modeling/layer-diagrams-reference.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|
|**Предметно-ориентированный язык**<br /><br /> Предметно-ориентированный язык представляет собой нотацию, разработанную для определенной цели. В Visual Studio обычно используется графическая нотация.<br /><br /> Типичные способы применения:<br /><br /> -Создание или настройка частей приложения. Разработка нотации и инструментов требует усилий. Результат может лучше соответствовать вашему домену, чем настройка языка UML.<br />-Крупные проекты или линейки продуктов, когда инвестиции в разработку языка DSL и его инструментов окупаются за счет его использования в нескольких проектах.<br /><br /> Пример<br /><br /> -   [Пакет SDK для моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Где можно получить дополнительные сведения?

[Форум по средствам моделирования и визуализации в Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>См. также

- [Новые возможности](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps и управление жизненным циклом приложений](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
