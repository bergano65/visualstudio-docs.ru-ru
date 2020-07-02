---
title: Визуализация кода | Документация Майкрософт
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
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532942"
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

|Сценарий|Статьи|
|-|-|
|**Анализ кода и его связей:**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.<br /><br /> **Примечание**. В этой версии Visual Studio термин *карта кода* используется вместо *графа зависимостей*.|-   [Сопоставьте зависимости в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Сопоставлять методы в стеке вызовов во время отладки](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Анализ структуры классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Описание высокоуровневой структуры системы и проверка кода на соответствие этой структуре:**<br /><br /> Опишите высокоуровневую структуру системы и ее предполагаемые зависимости, создав схемы слоев. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|-   [Создание схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)<br />-   [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)<br />-   [Проверка кода с помощью схем слоев](../modeling/validate-code-with-layer-diagrams.md)|
|**Передача требований пользователей и сведений об архитектуре:**<br /><br /> Смоделируйте требования пользователей и архитектуру программной системы, нарисовав схемы UML: схемы деятельности, компонентов, классов, последовательностей и вариантов использования.|-   [Создание моделей для приложения](../modeling/create-models-for-your-app.md)<br />-   [Требования к модели пользователя](../modeling/model-user-requirements.md)<br />-   [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|------------------|---------------|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Блоги**|[Блог по Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Технические статьи и журналы**|[Форум MSDN по архитектуре](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>См. также
 [Сценарий. изменение структуры с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [архитектура и архитектурное моделирование](../modeling/analyze-and-model-your-architecture.md) [Создание моделей для вашей модели приложения](../modeling/create-models-for-your-app.md) [требования пользователя](../modeling/model-user-requirements.md) [модель модели](../modeling/model-your-app-s-architecture.md) приложения [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)
