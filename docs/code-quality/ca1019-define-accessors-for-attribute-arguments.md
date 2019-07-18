---
title: CA1019. Определите методы доступа для аргументов атрибута
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e9491a608087565e84274d47c601b0629737d2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779354"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019. Определите методы доступа для аргументов атрибута

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 В своем конструкторе атрибут определяет аргументы, которые не имеют соответствующие свойства.

## <a name="rule-description"></a>Описание правила
 Атрибуты могут определять обязательные аргументы, которые должны быть указаны при применении атрибута к целевому объекту. Они также известны как позиционные аргументы, поскольку предоставляются для конструкторов атрибутов в качестве позиционных параметров. Для каждого обязательного аргумента атрибут должен предоставлять соответствующее свойство, доступное только для чтения, чтобы извлечь значение аргумента во время выполнения. Это правило проверяет, что для каждого параметра конструктора определено соответствующее свойство.

 Кроме того, атрибуты могут определять дополнительные параметры, известные как именованные аргументы. Эти аргументы предоставляются для конструкторов атрибутов по имени и должны иметь соответствующее свойство чтения/записи.

 Для обязательных и необязательных аргументов, соответствующие свойства и параметры конструктора следует использовать то же самое имя но другой регистр символов. Свойства используют Pascal, а для параметров используется смешанный регистр.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте свойство только для чтения для каждого параметра конструктора, который не имеет ни одного.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если не хотите, чтобы значение аргумент mandatory для них.

## <a name="custom-attributes-example"></a>Пример настраиваемых атрибутов

В следующем примере показано два атрибуты, определяющие обязательный параметр (позиционные). Первая реализация атрибута задано неправильно. Вторая реализация является верной.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Позиционные и именованные аргументы

Позиционные и именованные аргументы упрощают снимите флажок, чтобы потребители библиотеки обязательных атрибута и какие аргументы являются необязательными.

В следующем примере показана реализация атрибута, имеющего позиционные и именованные аргументы:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

В следующем примере показано, как применение пользовательского атрибута к двум свойствам:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1813: Избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также
 [Атрибуты](/dotnet/standard/design-guidelines/attributes)