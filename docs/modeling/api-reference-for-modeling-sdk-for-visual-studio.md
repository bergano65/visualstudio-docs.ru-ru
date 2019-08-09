---
title: Справочник по API для пакета SDK для моделирования
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 429ce6ed8d44387d3289ee7100da4e639f16ad8e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870590"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Справка по API SDK моделирования для Visual Studio

Пакет SDK моделирования и визуализации Visual Studio предоставляет платформу, на котором построены ваши средства доменного языка (DSL).

Этот раздел содержит справочные сведения о пространствах имен, имена которых начинаются с «Microsoft.VisualStudio.Modeling».

|Пространство имен|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Классы, такие как ModelElement, который является базовым классом для всех доменных классов, определенных вами в DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Классы, которые являются частью определения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Модель средства просмотра Store и производительности средств оценки.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Классы, такие как ShapeElement, который является базовым классом для всех фигур, которые определяют в DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Жест "и" Выбор методов.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API конструктора определения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Внутренние классы конструктора определения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Атрибуты, которые дают возможность расширение конструктора доменного языка с помощью команд, жестов и проверки.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Методы расширения для ModelElement, которые реализуют расширения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Атрибуты расширения|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Позволяет сделать части модели только для чтения.|
|[Microsoft. VisualStudio. моделирование. Интеграция](/previous-versions/ee904412(v=vs.140))|API Modelbus, который поможет вам интегрировать различные модели.|
|[Microsoft. VisualStudio. моделирование. Integration. средство выбора](/previous-versions/ee904394(v=vs.140))|Диалоговое окно, которое позволяет пользователям переходить к моделям и элементам следует создавать ссылки Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Служба выбора.|
|[Microsoft. VisualStudio. моделирование. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Платформа адаптеров Modelbus для Visual Studio.|
|[Microsoft. VisualStudio. моделирование. Integration. Shell. средство выбора](/previous-versions/ee886769(v=vs.140))|Диалоговое окно Выбор, позволяющий пользователям переходить к моделям и элементам следует создавать ссылки Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Интерфейс между доменными и Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Позволяет определить контекстном меню команд.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Позволяет определить ограничения проверки.|

## <a name="see-also"></a>См. также

- [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)
