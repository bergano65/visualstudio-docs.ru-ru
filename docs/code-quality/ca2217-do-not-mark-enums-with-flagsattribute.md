---
title: CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8afe63de8630b3fa7466e8c0784c26ba00bb1ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852483"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Видимый извне перечисление помечено <xref:System.FlagsAttribute>и он имеет один или несколько значений, не являющиеся степенями двух или сочетание этих определенных значений в перечислении.

## <a name="rule-description"></a>Описание правила

Перечисление должно иметь <xref:System.FlagsAttribute> присутствует, только в том случае, если каждое значение, определенных в перечислении равно степени двух или сочетание определенных значений.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите <xref:System.FlagsAttribute> из перечисления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example-that-should-not-have-the-attribute"></a>Пример, в котором не должен быть атрибут

В следующем примере показано перечисление, `Color`, который содержит значение 3. 3 не является степенью числа два или несколько определенных значений. `Color` Перечисления не должны быть помечены атрибутом <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Пример, в котором должен быть атрибут

В следующем примере показано перечисление, `Days`, который соответствует требованиям для с атрибутом <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.FlagsAttribute?displayProperty=fullName>
