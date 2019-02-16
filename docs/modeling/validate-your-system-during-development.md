---
title: Проверка системы в ходе разработки
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce0822f5731e7c09a6f6dff9116e70b97a529206
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316760"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.

 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи
 Для проверки программного обеспечения используйте приведенные ниже задачи.

|**Задачи**|**Связанные разделы**|
|-|-|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Создание схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|-|-|
|**Видеоролики**|![ссылка на видео](../data-tools/media/playvideo.gif) [Channel 9: Дуг: Понимание кода и разработка систем в Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif) [Channel 9: Создание архитектуры приложения с помощью схемы зависимостей](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif) [MSDN практические руководства: Проверка кода с помощью схем зависимостей](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Блоги**|-   [DevOps от Майкрософт](https://devblogs.microsoft.com/devops/)|
|**Технические статьи и журналы**|[Центр архитекторов на MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>См. также

- [Тестирование приложения](/azure/devops/test/overview?view=vsts)
- [Моделирование требований пользователей](../modeling/model-user-requirements.md)
- [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
