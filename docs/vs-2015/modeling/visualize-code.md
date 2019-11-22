---
title: Visualize code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 955103b6d28e90321fb45c23825f0c2a25362208
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301320"
---
# <a name="visualize-code"></a>Визуализация кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Пример:

- Чтобы понять связи в коде, сопоставьте их визуально.

- Для описания архитектуры системы и поддержания кода в согласованном состоянии с конструкцией создайте схемы слоев и проверьте код на соответствие этим схемам.

- Для описания структур классов создайте схемы классов.

- Чтобы смоделировать различные аспекты системы и сообщить информацию о них, нарисуйте схемы UML. Например, можно смоделировать компоненты системы, типы, взаимодействия и процессы.

  Кроме того, эти средства облегчают взаимодействие с другими участниками проекта. Например, можно использовать схемы классов UML для создания общего глоссария для обсуждения системы с заинтересованными лицами проекта, пользователями и членами команды.

  Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>Выберите действие

|||
|-|-|
|**Understand code and its relationships:**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.<br /><br /> **Примечание**. В этой версии Visual Studio термин *карта кода* используется вместо *графа зависимостей*.|-   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Map methods on the call stack while debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Understand class structures:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describe the high-level system design and validate code against this design:**<br /><br /> Опишите высокоуровневую структуру системы и ее предполагаемые зависимости, создав схемы слоев. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**Communicate the user requirements and architecture:**<br /><br /> Смоделируйте требования пользователей и архитектуру программной системы, нарисовав схемы UML: схемы деятельности, компонентов, классов, последовательностей и вариантов использования.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Links**|
|------------------|---------------|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Блоги**|[Блог по Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Технические статьи и журналы**|[MSDN Architecture Forum](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>См. также раздел
 [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md) [Model user requirements](../modeling/model-user-requirements.md) [Model your app's architecture](../modeling/model-your-app-s-architecture.md) [Use models in your development process](../modeling/use-models-in-your-development-process.md)
