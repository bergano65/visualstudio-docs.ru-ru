---
title: 'CA1028: хранилище enum должно иметь тип Int32 | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0b2e8ebcc7720f5cd9dc6c700bcc08b68f89e275
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542497"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028. Хранилище перечисляемых типов должно относиться к типу Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Базовый тип открытого перечисления — нет <xref:System.Int32?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Перечисление является типом значения, которое определяет набор связанных именованных констант. По умолчанию <xref:System.Int32?displayProperty=fullName> тип данных используется для хранения постоянного значения. Несмотря на то, что этот базовый тип можно изменить, он не является обязательным и не рекомендуется для большинства сценариев. Обратите внимание, что существенное увеличение производительности не достигается за счет использования типа данных меньше <xref:System.Int32> . Если нельзя использовать тип данных по умолчанию, следует использовать один из целочисленных типов, совместимых с CLS,,, или, <xref:System.Byte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> чтобы убедиться, что все значения перечисления могут быть представлены в языках программирования, совместимых с CLS.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, если не существует проблем с размером или совместимостью, используйте <xref:System.Int32> . В ситуациях, где недостаточно <xref:System.Int32> велик для хранения значений, используйте <xref:System.Int64> . Если для обратной совместимости требуется тип данных меньшего размера, используйте <xref:System.Byte> или <xref:System.Int16> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, только если это требуется для устранения проблем с обратной совместимостью. В приложениях сбой соответствия этому правилу обычно не вызывает проблем. В библиотеках, где требуется взаимодействие языков, несоблюдение этого правила может негативно сказаться на работе пользователей.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показаны два перечисления, которые не используют рекомендуемый базовый тип данных.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Пример исправления

### <a name="description"></a>Описание
 Следующий пример устраняет предыдущее нарушение, изменяя базовый тип данных на <xref:System.Int32> .

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1008. Перечисляемые типы должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027. Пометьте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700. Не присваивайте перечисляемым значениям имя Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712. Не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>См. также
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
