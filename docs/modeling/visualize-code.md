---
title: Визуализация кода
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 073a91e9bafca41192a12a20a7c06ff89644085f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663700"
---
# <a name="visualize-code"></a>Визуализация кода

Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Пример:

- Чтобы понять связи в коде, сопоставьте их визуально.

- Для описания архитектуры системы и сохранения кода в соответствии с его конструкцией создайте схемы зависимостей и проверьте код на соответствие этим схемам.

- Для описания структур классов создайте схемы классов.

Кроме того, эти средства облегчают взаимодействие с другими участниками проекта.

Чтобы узнать, какие выпуски Visual Studio поддерживают каждый компонент, см. статью [Поддержка выпуска для средств архитектуры и моделирования](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

## <a name="what-do-you-want-to-do"></a>Выберите действие

|||
|-|-|
|**Общие сведения о коде и его связях:**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.|- [сопоставлять зависимости в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />- [использования карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [методы Map в стеке вызовов во время отладки](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Общие сведения о структурах классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Опишите архитектуру высокоуровневой системы и проверяйте код в соответствии с этим дизайном:**<br /><br /> Опишите архитектуру системы высокого уровня и ее предполагаемые зависимости, создавая схемы зависимостей. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|- [создания схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)<br />[схемы зависимостей - : рекомендации](../modeling/layer-diagrams-guidelines.md)<br />- [проверки кода с помощью схем зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>См. также

- [Сценарий: изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Архитектура анализа и модели](../modeling/analyze-and-model-your-architecture.md)
- [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)
- [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
