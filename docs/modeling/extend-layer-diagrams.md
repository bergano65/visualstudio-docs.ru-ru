---
title: Расширение схем зависимостей
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04aa7c1948cd07bf49ab754619442e5310b023f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069138"
---
# <a name="extend-dependency-diagrams"></a>Расширение схем зависимостей
Можно написать код для создания и обновления схем зависимостей, а также для проверки структуры программного кода по схемам зависимостей в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

 Дополнительные сведения о диаграммах зависимостей см. в разделе:

-   [Схемы зависимостей: Справочник по](../modeling/layer-diagrams-reference.md)

-   [Схемы зависимостей: Рекомендации](../modeling/layer-diagrams-guidelines.md)

-   [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> Требования
 На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

-   Visual Studio

-   [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

-   Пакет SDK моделирования для Visual Studio


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 На компьютере, где планируется выполнять расширения слоев, должна быть установлена подходящая версия Visual Studio. Дополнительные сведения см. в разделе [развертывание расширения модели слоев](../modeling/deploy-a-layer-model-extension.md).

 Чтобы узнать, какие версии Visual Studio поддерживают схемы зависимостей, см. в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>В этом разделе
 [Добавление команд и жестов в схемы зависимостей](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Добавление пользовательской проверки архитектуры в схемы зависимостей](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Добавление пользовательских свойств в схемы зависимостей](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Перемещение по моделям слоев в коде программы и их обновление](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Развертывание расширения модели слоев](../modeling/deploy-a-layer-model-extension.md)

 [Устранение неполадок, связанных с расширениями для схем зависимостей](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>См. также

- [Схемы зависимостей: Справочник по](../modeling/layer-diagrams-reference.md)
- [Схемы зависимостей: Рекомендации](../modeling/layer-diagrams-guidelines.md)
- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
- [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)
