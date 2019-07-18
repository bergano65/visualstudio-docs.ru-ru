---
title: Справочник по API для пакета SDK для моделирования
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2cbf516b5ed999623c05e7f68656199363906bf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408445"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Справка по API SDK моделирования для Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK моделирования и визуализации Visual Studio предоставляет платформу, на котором строятся на предметно ориентированных языков (DSL) и средства UML.

> [!NOTE]
> Сведения об API моделирования UML, см. в разделе [Справочник по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Сведения о преобразования текста, см. в разделе [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md).

 Этот раздел содержит справочные сведения о пространствах имен, имена которых начинаются с «Microsoft.VisualStudio.Modeling».

|Пространство имен|Content|
|---------------|-------------|
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
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|API Modelbus, который поможет вам интегрировать различные модели.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Диалоговое окно, которое позволяет пользователям переходить к моделям и элементам следует создавать ссылки Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Служба выбора.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Платформа адаптеров Modelbus для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Диалоговое окно Выбор, позволяющий пользователям переходить к моделям и элементам следует создавать ссылки Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Интерфейс между DSL и [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Позволяет определить контекстном меню команд.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Позволяет определить ограничения проверки.|

## <a name="see-also"></a>См. также
 [Справочник по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md) [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)
