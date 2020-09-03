---
title: Справочник по API для моделирования SDK
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4be65a94892aa87dbc7f146ce3671336a37558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "76113735"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Справка по API SDK моделирования для Visual Studio

Пакет SDK визуализации и моделирования Visual Studio предоставляет платформу, на которой строятся средства доменных языков (DSL).

В этом разделе содержатся справочные материалы по пространствам имен, имена которых начинаются с Microsoft. VisualStudio. моделирование.

|Пространство имен|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Такие классы, как ModelElement, являются базовым классом для всех доменных классов, определенных в DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Классы, которые формируют часть определения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Средство просмотра хранилища моделей и средства измерения производительности.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Такие классы, как ShapeElement, являются базовым классом всех фигур, определенных в DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Жесты и методы выбора.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API конструктора определений DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Внутренние классы конструктора определений DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Атрибуты, позволяющие расширить конструктор DSL с помощью команд, жестов и проверки.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Методы расширения для ModelElement, реализующие расширяемость DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Атрибуты расширяемости|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Позволяет делать части модели только для чтения.|
|[Microsoft. VisualStudio. моделирование. Интеграция](/previous-versions/ee904412(v=vs.140))|API ModelBus, который помогает интегрировать различные модели.|
|[Microsoft. VisualStudio. моделирование. Integration. средство выбора](/previous-versions/ee904394(v=vs.140))|Диалоговое окно, позволяющее пользователям переходить к моделям и элементам для создания ссылок ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Служба выбора.|
|[Microsoft. VisualStudio. моделирование. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Платформа адаптера ModelBus для Visual Studio.|
|[Microsoft. VisualStudio. моделирование. Integration. Shell. средство выбора](/previous-versions/ee886769(v=vs.140))|Диалоговое окно выбора позволяет пользователям переходить к моделям и элементам для создания ссылок ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Интерфейс между DSL и Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Позволяет определять команды контекстного меню.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Позволяет определять ограничения проверки.|

## <a name="see-also"></a>См. также раздел

- [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)
