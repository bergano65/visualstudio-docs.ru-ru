---
title: CA1714. У перечислений флагов должны быть имена во множественном числе
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d71200c6c7fbb61e7994119fde5e75f7623fa669
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547193"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714. У перечислений флагов должны быть имена во множественном числе

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Перечисление имеет <xref:System.FlagsAttribute?displayProperty=fullName> и его имя не оканчивается на ".

По умолчанию это правило рассматривает только видимые извне перечисления, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Типы, помеченные с <xref:System.FlagsAttribute> помощью, имеют имена, которые являются во множественном числе, так как атрибут указывает, что может быть указано более одного значения. Например, перечисление, определяющее дни недели, может быть предназначено для использования в приложении, где можно указать несколько дней. Это перечисление должно <xref:System.FlagsAttribute> содержать и может называться "Days". Аналогичное перечисление, которое позволяет указать только один день, не будет иметь атрибута и может называться "Day".

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Сделайте имя перечисления словом множественного числа или удалите <xref:System.FlagsAttribute> атрибут, если не следует одновременно указывать несколько значений перечисления.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно спокойно подавлять нарушение, если имя является словом во множественном числе, но не заканчивается на ". Например, если перечисление с несколькими днями, описанное ранее, называлось "Дайсофсевик", это нарушает логику правила, но не его намерение. Такие нарушения следует подавлять.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (именование). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Связанные правила

- [CA1027 Пометьте перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Не помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Конструктор перечислений](/dotnet/standard/design-guidelines/enum)