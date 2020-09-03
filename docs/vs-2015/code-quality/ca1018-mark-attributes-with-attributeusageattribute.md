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
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535061"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018. Пометьте атрибуты с помощью AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>Атрибут отсутствует в пользовательском атрибуте.

## <a name="rule-description"></a>Описание правила
 При определении настраиваемого атрибута пометьте его с помощью, <xref:System.AttributeUsageAttribute> чтобы указать, где в исходном коде можно применить настраиваемый атрибут. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например, можно определить атрибут, определяющий лицо, ответственное за обслуживание и улучшение каждого типа в библиотеке, и эта ответственность всегда назначается на уровне типа. В этом случае компиляторы должны включить атрибут для классов, перечислений и интерфейсов, но не должны включать его в методах, событиях и свойствах. Политики и процедуры Организации определяют, должен ли атрибут быть включен для сборок.

 <xref:System.AttributeTargets?displayProperty=fullName>Перечисление определяет целевые объекты, которые можно указать для настраиваемого атрибута. Если опустить <xref:System.AttributeUsageAttribute> , пользовательский атрибут будет действителен для всех целевых объектов, как определено `All` значением <xref:System.AttributeTargets> перечисления.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute> . См. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Следует устранить нарушение этого правила, не исключая сообщение. Даже если атрибут наследуется <xref:System.AttributeUsageAttribute> , для упрощения обслуживания кода должен присутствовать атрибут.

## <a name="example"></a>Пример
 В следующем примере определяются два атрибута. `BadCodeMaintainerAttribute` неправильно опускает <xref:System.AttributeUsageAttribute> оператор и `GoodCodeMaintainerAttribute` правильно реализует атрибут, описанный ранее в этом разделе. Обратите внимание, что свойство `DeveloperName` является обязательным для правила разработки [CA1019: определяйте методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включается для полноты.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1019. Определите методы доступа для аргументов атрибута](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813. Избегайте незапечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также:
 [Атрибуты](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
