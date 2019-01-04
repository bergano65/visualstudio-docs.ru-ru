---
title: CA1714. У перечислений флагов должны быть имена во множественном числе
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf78041d61da991804a4dcdb0f924dc4a5f489e3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881817"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714. У перечислений флагов должны быть имена во множественном числе

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Общее перечисление имеет <xref:System.FlagsAttribute?displayProperty=fullName> и его имя не заканчивается в ".

## <a name="rule-description"></a>Описание правила
 Типы, помеченные атрибутом <xref:System.FlagsAttribute> имеют имена, которые используются во множественном числе, поскольку данный атрибут указывает, что можно указать более одного значения. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должны иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указать только один день не атрибут и не может быть вызван «Day».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Формируемая перечисления множественном или удалите <xref:System.FlagsAttribute> атрибута, если не следует одновременно указывать несколько значений перечисления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить нарушение, если имя во множественном числе word, но не заканчивается на ". Например если перечисление несколько дней, как было описано ранее назывались «DaysOfTheWeek», нарушит логику правило, но не его намерения. Подобные нарушения должны подавляться.

## <a name="related-rules"></a>Связанные правила
 [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Разработка перечислений](/dotnet/standard/design-guidelines/enum)