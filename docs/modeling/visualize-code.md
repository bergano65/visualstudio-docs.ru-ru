---
title: Визуализация кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 622655f1ed05ab77b36a3c4756a0176fcad74ac4
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684932"
---
# <a name="visualize-code"></a>Визуализация кода

Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Например:

- Чтобы понять связи в коде, сопоставьте их визуально.

- Для описания архитектуры системы и обеспечить соответствие со своей структурой кода, создание схем зависимостей и проверить код на соответствие этим схемам.

- Для описания структур классов создайте схемы классов.

Кроме того, эти средства облегчают взаимодействие с другими участниками проекта.

Чтобы узнать, какие выпуски Visual Studio поддерживают каждую функцию, см. в разделе [Edition поддержка для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Выберите действие

|||
|-|-|
|**Понимание кода и его отношений.**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.|- [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)<br />- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Сопоставление методов в стеке вызовов при отладке](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Анализ структуры классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Описания высокоуровневую структуру системы и проверить код на соответствие этой структуре:**<br /><br /> Опишите высокоуровневую структуру системы и ее предполагаемые зависимости, создание схем зависимостей. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|- [Создание схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Схемы зависимостей: Справочник по](../modeling/layer-diagrams-reference.md)<br />- [Схемы зависимостей: Рекомендации](../modeling/layer-diagrams-guidelines.md)<br />- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>См. также

- [Сценарий: Изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)
- [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)
- [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
