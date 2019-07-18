---
title: CA2132. Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ba13514ca886ab822367bbd61aaebdc8527ec45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545056"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132. Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия среды CLR, предназначенную для веб-приложения Silverlight).

## <a name="cause"></a>Причина

Атрибут прозрачности конструктора по умолчанию производного класса не такой критический, как прозрачность базового класса.

## <a name="rule-description"></a>Описание правила

Типы и члены с атрибутом <xref:System.Security.SecurityCriticalAttribute> не может использоваться кодом приложения Silverlight. Критичные в плане безопасности типы и элементы могут использоваться только надежным кодом в среде .NET Framework для библиотеки классов Silverlight. Поскольку открытая или защищенная конструкция в производном классе должна иметь ту же или большую прозрачность, чем ее базовый класс, класс в приложении не может быть производным от класса, помеченного как SecurityCritical.

Для кода платформы CoreCLR Если базовый тип имеет открытый или защищенный непрозрачный по умолчанию конструктор затем производный тип должен подчиняться правилам наследования конструктора по умолчанию. Производный тип также должен иметь конструктор по умолчанию, и этот конструктор должен быть по крайней мере конструктор критические по умолчанию базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение, удалите тип или не являются производными от типа не прозрачный с точки зрения безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не следует отключать предупреждения из этого правила. Нарушение этого правила в коде приложения приведет к CoreCLR отказывается загрузить тип с <xref:System.TypeLoadException>.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]