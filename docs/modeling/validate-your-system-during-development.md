---
title: Проверка системы в ходе разработки
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2b7d81b1f166e6cc97debc3291661d59ee6960
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594036"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки

Visual Studio поможет обеспечить соответствие программного обеспечения требованиям пользователей и архитектуры системы.

Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Ключевые задачи

Для проверки программного обеспечения выполните следующие действия.

|**Задачи**|**Связанные разделы**|
|-|-|
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br />Используйте требования и модели архитектуры для организации тестов системы и ее компонентов. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|- [разработки тестов из модели](../modeling/develop-tests-from-a-model.md)|
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br />Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|- [создания схем зависимостей из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />- [проверки кода с помощью схем зависимостей](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Внешние ресурсы

|**Категория**|**Links**|
|-|-|
|**Видеоролики**|![ссылки на видео](../data-tools/media/playvideo.gif) [Channel 9: Дуг семь: понимание кода и проектирование систем с помощью Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![ссылки на видео](../data-tools/media/playvideo.gif) [канал 9: создание архитектуры приложения](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Форумы**|- [Средства моделирования и визуализации Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [расширяемость Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>См. также:

- [Моделирование требований пользователей](../modeling/model-user-requirements.md)
- [Архитектура анализа и модели](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
