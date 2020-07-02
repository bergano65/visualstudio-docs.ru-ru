---
title: Визуализация кода
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9886ea905a4997d5735e4dd2cabbfc4798a5c4c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535880"
---
# <a name="visualize-code"></a>Визуализация кода

Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Пример:

- Чтобы понять связи в коде, сопоставьте их визуально.

- Для описания архитектуры системы и сохранения кода в соответствии с его конструкцией создайте схемы зависимостей и проверьте код на соответствие этим схемам.

- Для описания структур классов создайте схемы классов.

Кроме того, эти средства облегчают взаимодействие с другими участниками проекта.

Чтобы узнать, какие выпуски Visual Studio поддерживают каждый компонент, см. статью [Поддержка выпуска для средств архитектуры и моделирования](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

## <a name="what-do-you-want-to-do"></a>Выберите действие

|Сценарий|Статьи|
|-|-|
|**Анализ кода и его связей:**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.|- [Сопоставьте зависимости в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Сопоставлять методы в стеке вызовов во время отладки](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Анализ структуры классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Описание высокоуровневой структуры системы и проверка кода на соответствие этой структуре:**<br /><br /> Опишите архитектуру системы высокого уровня и ее предполагаемые зависимости, создавая схемы зависимостей. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|- [Создание схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)<br />- [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)<br />- [Проверка кода с помощью схем зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>См. также

- [Сценарий: изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Архитектура анализа и модели](../modeling/analyze-and-model-your-architecture.md)
- [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)
- [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
