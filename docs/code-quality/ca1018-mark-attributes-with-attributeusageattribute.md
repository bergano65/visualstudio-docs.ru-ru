---
title: CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: dfdaca64c166a29ad731719f79bbad57e975ff8b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55043730"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> Атрибут отсутствует в пользовательском атрибуте.

## <a name="rule-description"></a>Описание правила
 При определении настраиваемого атрибута, пометьте его с помощью <xref:System.AttributeUsageAttribute> для указания, где в исходном коде пользовательский атрибут может применяться. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например можно определить атрибут, который позволяет определить лицо, кто отвечает за обслуживание и расширение каждого типа в библиотеке, а ответственность всегда назначается на уровне типа. В этом случае компиляторы следует включить атрибут на классы, перечисления и интерфейсы, но не следует включать ее на методы, события или свойства. Организационными политиками и процедурами будет определяться ли атрибут для сборки.

 <xref:System.AttributeTargets?displayProperty=fullName> Перечисление определяет целевые объекты, которые можно задать для настраиваемого атрибута. Если опустить <xref:System.AttributeUsageAttribute>, пользовательского атрибута будет применяться для всех целевых объектов, как определено `All` значение <xref:System.AttributeTargets> перечисления.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>. См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Следует устранить нарушение этого правила, а не за исключением сообщения. Даже если атрибут наследует <xref:System.AttributeUsageAttribute>, чтобы упростить обслуживание кода должен присутствовать атрибут.

## <a name="example"></a>Пример
 В следующем примере определяется два атрибута. `BadCodeMaintainerAttribute` неправильно опускает <xref:System.AttributeUsageAttribute> инструкции и `GoodCodeMaintainerAttribute` правильно реализует атрибут, который описан ранее в этом разделе. Обратите внимание, что свойство `DeveloperName` требуется правило проектирования [CA1019 необходимо: Определять методы доступа для аргументов атрибута](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включен для обеспечения полноты.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1019: НЕОБХОДИМО Определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также

- [Атрибуты](/dotnet/standard/design-guidelines/attributes)