---
title: 'CA1018: Пометка атрибутов с помощью AttributeUsageAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 404ef250726d12300e2b72150ff42b4f0b7bfb24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662049"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: помечайте атрибуты как AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Атрибут <xref:System.AttributeUsageAttribute?displayProperty=fullName> отсутствует в пользовательском атрибуте.

## <a name="rule-description"></a>Описание правила
 При определении настраиваемого атрибута пометьте его с помощью <xref:System.AttributeUsageAttribute>, чтобы указать, где в исходном коде можно применить настраиваемый атрибут. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например, можно определить атрибут, определяющий лицо, ответственное за обслуживание и улучшение каждого типа в библиотеке, и эта ответственность всегда назначается на уровне типа. В этом случае компиляторы должны включить атрибут для классов, перечислений и интерфейсов, но не должны включать его в методах, событиях и свойствах. Политики и процедуры Организации определяют, должен ли атрибут быть включен для сборок.

 Перечисление <xref:System.AttributeTargets?displayProperty=fullName> определяет целевые объекты, которые можно указать для настраиваемого атрибута. Если опустить <xref:System.AttributeUsageAttribute>, пользовательский атрибут будет действителен для всех целевых объектов, как определено `All` значением перечисления <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>. См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Следует устранить нарушение этого правила, не исключая сообщение. Даже если атрибут наследует <xref:System.AttributeUsageAttribute>, для упрощения обслуживания кода должен присутствовать атрибут.

## <a name="example"></a>Пример
 В следующем примере определяются два атрибута. `BadCodeMaintainerAttribute` неправильно пропускает инструкцию <xref:System.AttributeUsageAttribute>, и `GoodCodeMaintainerAttribute` правильно реализует атрибут, описанный ранее в этом разделе. Обратите внимание, что свойство `DeveloperName` требуется для правила разработки [CA1019: определяйте методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включается для полноты.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также раздел
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
