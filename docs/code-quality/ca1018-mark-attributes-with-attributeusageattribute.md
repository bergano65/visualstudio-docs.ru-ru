---
title: CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 78917bcd4c67e1da205595bac07c8e0e5947318d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923056"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
<xref:System.AttributeUsageAttribute?displayProperty=fullName> Атрибут отсутствует в пользовательском атрибуте.

## <a name="rule-description"></a>Описание правила
При определении настраиваемого атрибута пометьте его с помощью <xref:System.AttributeUsageAttribute> , чтобы указать, где в исходном коде можно применить настраиваемый атрибут. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например, можно определить атрибут, определяющий лицо, ответственное за обслуживание и улучшение каждого типа в библиотеке, и эта ответственность всегда назначается на уровне типа. В этом случае компиляторы должны включить атрибут для классов, перечислений и интерфейсов, но не должны включать его в методах, событиях и свойствах. Политики и процедуры Организации определяют, должен ли атрибут быть включен для сборок.

<xref:System.AttributeTargets?displayProperty=fullName> Перечисление определяет целевые объекты, которые можно указать для настраиваемого атрибута. Если опустить <xref:System.AttributeUsageAttribute>, пользовательский атрибут будет действителен для всех целевых объектов, как определено `All` значением <xref:System.AttributeTargets> перечисления.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>. См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Следует устранить нарушение этого правила, не исключая сообщение. Даже если атрибут наследуется <xref:System.AttributeUsageAttribute>, для упрощения обслуживания кода должен присутствовать атрибут.

## <a name="example"></a>Пример
В следующем примере определяются два атрибута. `BadCodeMaintainerAttribute`неправильно опускает <xref:System.AttributeUsageAttribute> оператор и `GoodCodeMaintainerAttribute` правильно реализует атрибут, описанный ранее в этом разделе. Обратите внимание, `DeveloperName` что свойство является обязательным для правила [разработки CA1019: Определите методы доступа для аргументов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) атрибутов и включается для полноты.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1019 Определение методов доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813 Избегайте использования незапечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)