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
ms.openlocfilehash: 9fb9810f1c212dfb881f5725676a79c6307b9cfa
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476505"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки

Visual Studio помогает привести в соответствие программное обеспечение требований пользователей и архитектуру системы.

Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи

Для проверки программного обеспечения можно используйте следующие задачи:

|**Задачи**|**Связанные разделы**|
|-|-|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br />Чтобы организовать тесты системы и ее компонентов можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|- [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br />Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|- [Создание схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Ссылки**|
|-|-|
|**Видеоролики**|![ссылка на видео](../data-tools/media/playvideo.gif) [Channel 9: Дуг: Понимание кода и разработка систем в Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif) [Channel 9: Создание архитектуры приложения](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Форумы**|- [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Расширяемость Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>См. также

- [Моделирование требований пользователей](../modeling/model-user-requirements.md)
- [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
