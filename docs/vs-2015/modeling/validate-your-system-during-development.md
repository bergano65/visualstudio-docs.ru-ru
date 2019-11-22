---
title: Validate your system during development | Microsoft Docs
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
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301344"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи
 Для проверки программного обеспечения используйте приведенные ниже задачи.

|**Задачи**|**Связанные разделы**|
|---------------|---------------------------|
|**Make sure your model is consistent:**<br /><br /> В зависимости от способа использования и интерпретации моделей в проекте может оказаться полезным запретить некоторые сочетания элементов. Например, в качестве ограничения для классов UML можно потребовать их обязательного соответствия [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Подобные ограничения можно определять в расширениях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Validate your UML model](../modeling/validate-your-uml-model.md)<br />-   [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Develop tests from a model](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы слоев описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Links**|
|------------------|---------------|
|**Видеоролики**|![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: Code Understanding and System Design with Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Architecting an Application using a Layer Diagram](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: How to Validate Code using Layer Diagrams](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Блоги**|-   [Блог по Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Технические статьи и журналы**|[Центр архитекторов на MSDN](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>См. также раздел
 [Testing the application](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Model user requirements](../modeling/model-user-requirements.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md)
