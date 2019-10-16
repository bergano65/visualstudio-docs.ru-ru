---
title: 'CA1028: хранилище перечислений должно иметь тип Int32'
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
ms.openlocfilehash: 2b963f831637e357126137cf40b0d6c9e9a4f8b8
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349120"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: хранилище перечислений должно иметь тип Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Базовый тип перечисления не <xref:System.Int32?displayProperty=fullName>.

По умолчанию это правило рассматривает только общедоступные перечисления, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию для хранения постоянного значения используется тип данных <xref:System.Int32?displayProperty=fullName>. Несмотря на то, что этот базовый тип можно изменить, он не является обязательным и не рекомендуется для большинства сценариев. Не достигается значительного увеличения производительности с использованием типа данных, размер которого меньше <xref:System.Int32>. Если нельзя использовать тип данных по умолчанию, следует использовать один из целочисленных типов, совместимых с CLS, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> или <xref:System.Int64>, чтобы убедиться в том, что все значения перечисления можно представить в соответствии с CLS-совместимым программированием. Языки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, если не существует проблем с размером или совместимостью, используйте <xref:System.Int32>. В ситуациях, где значение <xref:System.Int32> недостаточно велико для хранения значений, используйте <xref:System.Int64>. Если для обратной совместимости требуется тип данных меньшего размера, используйте <xref:System.Byte> или <xref:System.Int16>.

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

- [CA1008: перечисляемые типы должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217.md)
- [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>