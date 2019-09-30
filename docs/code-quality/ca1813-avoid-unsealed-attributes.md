---
title: CA1813. Избегайте незапечатанных атрибутов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233594"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813. Избегайте незапечатанных атрибутов

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Категория|Microsoft. Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Открытый тип наследует от <xref:System.Attribute?displayProperty=fullName>, не является абстрактным и не запечатан (`NotInheritable` в Visual Basic).

## <a name="rule-description"></a>Описание правила

.NET предоставляет методы для извлечения пользовательских атрибутов. По умолчанию эти методы осуществляют поиск иерархии наследования атрибутов. Например, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> ищет указанный тип атрибута или любой тип атрибута, который расширяет указанный тип атрибута. Запечатывание атрибута позволяет исключить Поиск через иерархию наследования и повысить производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, запечатайте тип атрибута или сделайте его абстрактным.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

В этом правиле можно отключить вывод предупреждений. Подавлять, только если вы определяете иерархию атрибута и не можете запечатывать атрибут или сделать его абстрактным.

## <a name="example"></a>Пример

В следующем примере показан настраиваемый атрибут, который удовлетворяет этому правилу.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1019 Определение методов доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018 Пометка атрибутов с помощью AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)