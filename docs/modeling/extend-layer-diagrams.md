---
title: Расширение схем зависимостей
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301491"
---
# <a name="extend-dependency-diagrams"></a>Расширение схем зависимостей

Можно написать код для создания и обновления диаграмм зависимости и проверки структуры кода программы на диаграммах зависимостей в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

## <a name="requirements"></a>Требования

На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

- Visual Studio

- [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

- Моделирование SDK для визуальной студии

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Вы должны иметь подходящее издание Visual Studio установлен на компьютере, где вы хотите запустить ваш слой расширений. Чтобы узнать, какие издания Visual Studio поддерживают [Edition support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)диаграммы зависимости, см.

## <a name="see-also"></a>См. также раздел

- [Схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)
- [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)
- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)
