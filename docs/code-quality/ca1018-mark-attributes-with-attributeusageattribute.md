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
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306134"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Атрибут <xref:System.AttributeUsageAttribute?displayProperty=fullName> отсутствует в пользовательском атрибуте.

## <a name="rule-description"></a>Описание правила
При определении настраиваемого атрибута пометьте его с помощью <xref:System.AttributeUsageAttribute>, чтобы указать, где в исходном коде можно применить настраиваемый атрибут. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например, можно определить атрибут, определяющий лицо, ответственное за обслуживание и улучшение каждого типа в библиотеке, и эта ответственность всегда назначается на уровне типа. В этом случае компиляторы должны включить атрибут для классов, перечислений и интерфейсов, но не должны включать его в методах, событиях и свойствах. Политики и процедуры Организации определяют, должен ли атрибут быть включен для сборок.

Перечисление <xref:System.AttributeTargets?displayProperty=fullName> определяет целевые объекты, которые можно указать для настраиваемого атрибута. Если опустить <xref:System.AttributeUsageAttribute>, пользовательский атрибут будет действителен для всех целевых объектов, как определено значением `All` перечисления <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>. См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Следует устранить нарушение этого правила, не исключая сообщение. Даже если атрибут наследует <xref:System.AttributeUsageAttribute>, для упрощения обслуживания кода должен присутствовать атрибут.

## <a name="example"></a>Пример
В следующем примере определяются два атрибута. `BadCodeMaintainerAttribute` неправильно опускает оператор <xref:System.AttributeUsageAttribute>, а `GoodCodeMaintainerAttribute` правильно реализует атрибут, описанный ранее в этом разделе. Обратите внимание, что в правиле проектирования [CA1019 требуется свойство @no__t: Определите методы доступа для аргументов атрибута @ no__t-0 и включается для полноты.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Связанные правила
@NO__T 0CA1019: Определение методов доступа для аргументов атрибутов @ no__t-0

@NO__T 0CA1813: Не используйте незапечатанные атрибуты @ no__t-0

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)