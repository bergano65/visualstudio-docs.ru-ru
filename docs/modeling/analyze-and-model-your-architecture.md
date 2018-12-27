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
ms.openlocfilehash: 0e9dd37f3db5bc231a831879d2620ad55a50c3b7
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740449"
---
# <a name="analyze-and-model-your-architecture"></a>Анализ и моделирование архитектуры

Убедитесь, что ваше приложение требованиям архитектуры с помощью архитектуры Visual Studio и инструментов для разработки и моделирования приложения моделирования.

* Visual Studio поможет вам визуализировать структуру, поведение и отношения кода и разобраться в имеющемся программном коде.

* Обучить команды в необходимости за соблюдение архитектурных зависимостей.

* Программа позволяет создавать модели с разным уровнем детализации на протяжении всего жизненного цикла приложения.

См. в разделе [сценария: Изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>Кому

|||
|-|-|
|**Визуализация кода**<br /><br /> — См. в разделе организации и отношений в коде путем создания карт кода. Визуализация зависимостей между сборками, пространствами имен, классами, методами и т. д.<br />— См. в разделе структуры и членов классов для конкретного проекта путем создания схем классов из кода.<br />-Найти конфликты между кодом и дизайном путем создания схем зависимостей для проверки кода.|-   [Визуализация кода](../modeling/visualize-code.md)<br />-   [Работа с классами и другими типами (конструктор классов)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />-   [Видео: Понимание разработки из кода с помощью карт кода Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Видео: Проверка зависимостей архитектуры в режиме реального времени](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Определение архитектуры**<br /><br /> — Определение и наложение ограничений на зависимости между компонентами кода путем создания схем зависимостей.|-   [Видео: Проверка зависимостей архитектуры с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Проверка системы на соответствие требованиям и намеченной структуре**<br /><br /> — Проверка зависимостей кода с помощью схем зависимостей, которые описывают предполагаемую архитектуру и предотвратить изменения, которые могут конфликтовать с проектом.|-   [Видео: Проверка зависимостей архитектуры с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Настройка моделей и схем**<br /><br /> -Создание собственных доменных языков.|-   [Пакет SDK моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Создание текстов с помощью шаблонов T4**<br /><br /> -Использование блоков текста и контроль логики внутри шаблонов для создания текстовых файлов.<br /> -Сборки шаблонов T4 с помощью MSBuild, входящих в Visual Studio|-   [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Совместное использование моделей, схем и карт кода с помощью системы управления версиями Team Foundation**<br /><br /> -Поместить карт кода, проектов и схем зависимостей в системе управления версиями Team Foundation, вы можете использовать их.| |

Чтобы узнать, какие выпуски Visual Studio поддерживают каждую функцию, см. в разделе [Edition поддержка для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Типы моделей и типичные способы применения

### <a name="code-maps"></a>Карты кода
Карты кода помогают увидеть структуру кода и имеющиеся в нем отношения.

**Типичные способы применения:**

-   Изучите программный код, чтобы лучше понять его структуру и зависимости, порядок обновления и расчетную стоимость реализации предлагаемых изменений.

**См. в разделе:**

-   [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)
-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Диаграмма зависимостей
Схемы зависимостей позволяют определить структуру приложения как набор слоев или блоков с явно заданными зависимостями. Можно выполнить проверку для обнаружения конфликтов между зависимостями в коде и зависимостями, описанными в схеме зависимостей.

**Типичные способы применения:**

-   Стабилизация структуры приложения путем внесения многочисленных изменений на протяжении его жизненного цикла.
-   Выявление непредвиденных конфликтов зависимостей до возвращения внесенных в код изменений.

**См. в разделе:**

-   [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
-   [Схемы зависимостей: Справочник по](../modeling/layer-diagrams-reference.md)
-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Предметно-ориентированный язык
Предметно-ориентированный язык представляет собой нотацию, разработанную для определенной цели. В Visual Studio обычно используется графическая нотация.

**Типичные способы применения:**

-   Создание или настройка частей приложения. Разработка нотации и инструментов требует усилий. Результат может лучше соответствовать вашему домену, чем настройка языка UML.
-   Крупные проекты или линейки продуктов, когда инвестиции в разработку языка DSL и его инструментов окупаются за счет его использования сразу в нескольких проектах.

**См. в разделе:**

-   [SDK моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>Где можно получить дополнительные сведения?

[Форум по средствам моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>См. также

- [Новые возможности](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps и управление жизненным циклом приложений](/azure/devops/user-guide/devops-alm-overview)
