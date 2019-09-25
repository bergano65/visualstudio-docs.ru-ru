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
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232331"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132. Конструкторы по умолчанию должны быть по меньшей мере такими же критическими, как конструкторы по умолчанию базового типа

|||
|-|-|
|TypeName|дефаултконструкторсмуссавеконсистенттранспаренци|
|CheckId|CA2132|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия CLR, относящаяся к веб-приложениям Silverlight).

## <a name="cause"></a>Причина:

Атрибут прозрачности конструктора по умолчанию производного класса не так важен, как прозрачность базового класса.

## <a name="rule-description"></a>Описание правила

Типы и члены, имеющие, <xref:System.Security.SecurityCriticalAttribute> не могут использоваться кодом приложения Silverlight. Критичные в плане безопасности типы и элементы могут использоваться только надежным кодом в среде .NET Framework для библиотеки классов Silverlight. Поскольку открытая или защищенная конструкция в производном классе должна иметь ту же или большую прозрачность, чем ее базовый класс, класс в приложении не может быть производным от класса, помеченного как SecurityCritical.

Для кода платформы CoreCLR, если базовый тип имеет открытый или защищенный непрозрачный конструктор по умолчанию, производный тип должен соблюдать правила наследования конструктора по умолчанию. Производный тип также должен иметь конструктор по умолчанию, и этот конструктор должен быть по крайней мере критическим конструктором по умолчанию базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение, удалите тип или не наследовать от непрозрачного типа безопасности.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте вывод предупреждений из этого правила. Нарушения этого правила в коде приложения приведут к тому, что CoreCLR отказывается загрузить тип с помощью <xref:System.TypeLoadException>.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]