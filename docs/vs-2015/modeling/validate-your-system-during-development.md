---
title: Проверка системы во время разработки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586266"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи
 Для проверки программного обеспечения используйте приведенные ниже задачи.

|**Задачи**|**Связанные разделы**|
|---------------|---------------------------|
|**Убедитесь в непротиворечивости модели:**<br /><br /> В зависимости от способа использования и интерпретации моделей в проекте может оказаться полезным запретить некоторые сочетания элементов. Например, в качестве ограничения для классов UML можно потребовать их обязательной совместимости с [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Подобные ограничения можно определять в расширениях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Проверка модели UML](../modeling/validate-your-uml-model.md)<br />-   [Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы слоев описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Создание схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Проверка кода с помощью схем слоев](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|------------------|---------------|
|**Видео**|![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Дуг семь: понимание кода и проектирование систем с помощью Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") - [канал 9. Создание архитектуры приложения с помощью схемы слоев](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [серия практических руководств MSDN: как проверить код с помощью схем слоев](https://msdn.microsoft.com/vstudio/gg501755)|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Блоги**|-   [Блог Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Технические статьи и журналы**|[Центр архитекторов на MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>См. также:
 [Тестирование приложения](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md) [модель схемы требования пользователей](../modeling/model-user-requirements.md) [анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)
