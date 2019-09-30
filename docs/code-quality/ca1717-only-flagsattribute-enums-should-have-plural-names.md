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
ms.openlocfilehash: b352d8f49cb92f70b449427179229fd882dbc9ce
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234061"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717. Только перечисления FlagsAttribute должны иметь имена во множественном числе

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Имя перечисления заканчивается словом во множественном числе, а перечисление не помечено <xref:System.FlagsAttribute?displayProperty=fullName> атрибутом.

По умолчанию это правило рассматривает только видимые извне перечисления, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Соглашения об именовании определяют, что имя перечисления во множественном числе указывает, что можно одновременно указать несколько значений перечисления. <xref:System.FlagsAttribute> Сообщает компилятору, что перечисление следует рассматривать как битовое поле, которое включает побитовые операции перечисления.

Если в каждый момент времени может быть указано только одно значение перечисления, то имя перечисления должно быть словом в единственном числе. Например, перечисление, определяющее дни недели, может быть предназначено для использования в приложении, где можно указать несколько дней. Это перечисление должно <xref:System.FlagsAttribute> содержать и может называться "Days". Аналогичное перечисление, которое позволяет указать только один день, не будет иметь атрибута и может называться "Day".

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает время, необходимое для изучения новой библиотеки программного обеспечения, и повышает уверенность клиентов в том, что библиотека была разработана пользователями, обладающими опытом в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Сделайте имя перечисления словом в единственном числе или добавьте <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из правила, если имя заканчивается в единственном слове.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (именование). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Связанные правила

- [CA1714 Перечисления flags должны иметь имена во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027 Пометьте перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Не помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Конструктор перечислений](/dotnet/standard/design-guidelines/enum)