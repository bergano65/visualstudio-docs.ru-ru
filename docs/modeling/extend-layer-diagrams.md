---
title: Расширение схем зависимостей
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c164174b88ca9fdd815668084c1447e20de072c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476566"
---
# <a name="extend-dependency-diagrams"></a>Расширение схем зависимостей

Можно написать код для создания и обновления схем зависимостей и для проверки структуры программного кода по схемам зависимостей в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

## <a name="requirements"></a>Требования

На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

- Visual Studio

- [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

- Пакет SDK моделирования для Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Необходимо иметь подходящий выпуск Visual Studio, установленной на компьютере, где вы хотите выполнять расширения слоев. Чтобы узнать, какие выпуски Visual Studio поддерживают схемы зависимостей, см. в разделе [Edition поддержка для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>См. также

- [Схемы зависимостей: справочник](../modeling/layer-diagrams-reference.md)
- [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)
- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)
