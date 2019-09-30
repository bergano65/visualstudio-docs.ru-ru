---
title: CA1028. Хранилище перечисляемых типов должно относиться к типу Int32
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 47a934a6e35296927eea64465ff8e7007219bec5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236085"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028. Хранилище перечисляемых типов должно относиться к типу Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Базовый тип перечисления — нет <xref:System.Int32?displayProperty=fullName>.

По умолчанию это правило рассматривает только общедоступные перечисления, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию <xref:System.Int32?displayProperty=fullName> тип данных используется для хранения постоянного значения. Несмотря на то, что этот базовый тип можно изменить, он не является обязательным и не рекомендуется для большинства сценариев. Не достигается значительного выигрыша в производительности за счет использования типа данных меньше <xref:System.Int32>. Если нельзя использовать тип данных по умолчанию, следует использовать один из целочисленных типов, совместимых с <xref:System.Byte>CLS, <xref:System.Int32>, <xref:System.Int16>, или <xref:System.Int64> , чтобы убедиться, что все значения перечисления могут быть представлены в CLS-совместимые языки программирования.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, если не существует проблем с размером или совместимостью, <xref:System.Int32>используйте. В ситуациях, <xref:System.Int32> где недостаточно велик для хранения значений, используйте. <xref:System.Int64> Если для обратной совместимости требуется тип данных меньшего <xref:System.Byte> размера <xref:System.Int16>, используйте или.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Подавлять предупреждение из этого правила, только если это требуется для устранения проблем с обратной совместимостью. В приложениях сбой соответствия этому правилу обычно не вызывает проблем. В библиотеках, где требуется взаимодействие языков, несоблюдение этого правила может негативно сказаться на работе пользователей.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Пример нарушения

В следующем примере показаны два перечисления, которые не используют рекомендуемый базовый тип данных.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Пример исправления

Следующий пример устраняет предыдущее нарушение, изменяя базовый тип данных на <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1008 Перечисляемые типы должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027 Пометьте перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Не помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Не наименование значений enum "reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Не добавляйте значения перечисления в качестве префикса имени типа](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>