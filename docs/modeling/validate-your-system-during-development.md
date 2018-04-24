---
title: Проверка системы в ходе разработки
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d4ebc815f474f1b8a1c59c9736f9014ba02e523
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи
 Для проверки программного обеспечения используйте приведенные ниже задачи.

|**Задачи**|**Связанные разделы**|
|---------------|---------------------------|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Разработка тестов на основе модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Создание схемы зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|------------------|---------------|
|**Видеоролики**|![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: семь дуг: Общие сведения о код и Дизайн системы с помощью Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: архитектуры приложения с помощью диаграммы зависимостей](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [MSDN практические руководства: проверка кода, с помощью схемы зависимостей](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Блоги**|-   [Блог по Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Технические статьи и журналы**|[Центр архитекторов на MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>См. также

- [Тестирование приложения](https://www.visualstudio.com/en-gb/docs/test/overview)
- [Моделирование требований пользователей](../modeling/model-user-requirements.md)
- [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
