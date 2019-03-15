---
title: CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6da5a791237aefa037b2cb16bffef34576ac6e7
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869875"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя перечисления заканчивается на слова во множественном числе и перечисления не помечен атрибутом <xref:System.FlagsAttribute?displayProperty=fullName> атрибута.

По умолчанию это правило считывает только видимое извне перечисления, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Соглашения об именовании диктовать, что множественное число имени перечисления указывает, что более одного значения перечисления могут быть заданы одновременно. <xref:System.FlagsAttribute> Сообщает компилятору, что перечисление должно рассматриваться как битовое поле, которое позволяет побитовых операций над перечисления.

Если только одно значение перечисления можно указать за раз, имя перечисления должно быть словом в единственном числе. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должны иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указать только один день не атрибут и не может быть вызван «Day».

Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Формируемая перечисления словом в единственном числе, или добавьте <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из правила, если имя функции оканчивается словом в единственном числе.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1717.api_surface = private, internal
```

Этот параметр для только что это правило, для всех правил или для всех правил можно настроить в этой категории (именования). Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Связанные правила

- [CA1714: Перечислений флагов должны быть имена во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Разработка перечислений](/dotnet/standard/design-guidelines/enum)