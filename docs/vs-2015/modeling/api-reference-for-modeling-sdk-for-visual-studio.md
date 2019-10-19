---
title: Справочник по API для моделирования SDK
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672847"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Справка по API SDK моделирования для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK визуализации и моделирования Visual Studio предоставляет платформу, в которой строятся доменные языки (DSL) и средства UML.

> [!NOTE]
> Дополнительные сведения об API моделирования UML см. в [справочнике по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Дополнительные сведения о преобразовании текста см. в разделе [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md).

 В этом разделе содержатся справочные материалы по пространствам имен, имена которых начинаются с Microsoft. VisualStudio. моделирование.

|Пространство имен|Content|
|---------------|-------------|
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
|[Microsoft. VisualStudio. моделирование. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Платформа адаптера ModelBus для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Microsoft. VisualStudio. моделирование. Integration. Shell. средство выбора](/previous-versions/ee886769(v=vs.140))|Диалоговое окно выбора позволяет пользователям переходить к моделям и элементам для создания ссылок ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Интерфейс между DSL и [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Позволяет определять команды контекстного меню.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Позволяет определять ограничения проверки.|

## <a name="see-also"></a>См. также

- [Справочник по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)
