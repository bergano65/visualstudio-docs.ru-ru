---
title: Справка по API SDK моделирования для Visual Studio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5b4f6a5738d60cf83d1b886161cc3dfa2ea1c452
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Справка по API SDK моделирования для Visual Studio

Пакет SDK моделирования и визуализации в Visual Studio предоставляет платформу, на которой строятся средства доменного языка (DSL).

Этот раздел содержит справочные материалы для пространств имен, имена которых начинаются с «Microsoft.VisualStudio.Modeling».

|Пространство имен|Content|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Классы, такие как ModelElement, который является базовым классом для всех классов домена, которые определяются в доменный язык DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Классы, являющиеся частью определения доменного языка.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Средство просмотра хранилища и производительности измерения средства модели.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Классы, такие как ShapeElement, который является базовым классом для всех фигур, которые указываются в DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Выбор и жестов методы.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|API определения DSL конструктора.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Внутренние классы конструктора определения DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Атрибуты, которые позволяют расширить конструктор DSL с команд, жестов и проверки.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Методы расширения для ModelElement, реализующих DSL расширяемости.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Расширения атрибутов|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Позволяет сделать части модели только для чтения.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|В Modelbus API, который позволяет интегрировать разных моделей.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Диалоговое окно, которое позволяет пользователям переходить к модели и элементы для создания ссылок Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Служба выбора.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Платформа адаптеров Modelbus для Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Диалоговое окно Выбор, позволяющий пользователям переходить к модели и элементы для создания ссылок Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Интерфейс между доменными и Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Позволяет определить контекстном меню команд.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Позволяет определить ограничения проверки.|

## <a name="see-also"></a>См. также

- [Настройка преобразования текста T4](../modeling/customizing-t4-text-transformation.md)
