---
title: 'CA1018: Пометьте атрибуты с помощью AttributeUsageAttribute | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfb9e7d954697fab554749dbd42155f92030ce88
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591330"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: помечайте атрибуты как AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1018: пометьте атрибуты с помощью AttributeUsageAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1018-mark-attributes-with-attributeusageattribute).

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
 В следующем примере определяется два атрибута. `BadCodeMaintainerAttribute` неправильно опускает <xref:System.AttributeUsageAttribute> инструкции и `GoodCodeMaintainerAttribute` правильно реализует атрибут, который описан ранее в этом разделе. Обратите внимание, что свойство `DeveloperName` требуется правило проектирования [CA1019 необходимо: определять методы доступа для аргументов атрибута](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включен для обеспечения полноты.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также
 [Атрибуты](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



