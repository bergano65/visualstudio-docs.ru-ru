---
title: 'CA1019: необходимо определять методы доступа для аргументов атрибутов'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56354e4d0d6bf3ed381cb077cc0ed9c9a41d4843
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: необходимо определять методы доступа для аргументов атрибутов
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

 Для обязательных и необязательных аргументов соответствующие свойства и параметры конструктора следует использовать то же имя, но в разных регистрах. Свойства используют Pascal регистр символов и параметров используйте camel регистра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, добавьте свойство только для чтения для каждого параметра конструктора, который не имеет ни одного.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавляет предупреждение из этого правила, если не требуется значение обязательного аргумента для извлечения.

## <a name="custom-attributes-example"></a>Пример настраиваемых атрибутов

### <a name="description"></a>Описание
 В следующем примере показано два атрибута, определяющих обязательный параметр (позиционные). Первый реализации атрибута задано неправильно. Реализация второго правильно работает.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Позиционные и именованные аргументы

### <a name="description"></a>Описание
 Позиционные и именованные аргументы упрощают для пользователей библиотеки обязательных атрибута и какие аргументы являются необязательными.

 В следующем примере показана реализация атрибута, который использует позиционные и именованные аргументы.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

### <a name="comments"></a>Комментарии
 В следующем примере показано, как применение настраиваемого атрибута к двум свойствам.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1813: избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>См. также
 [Атрибуты](/dotnet/standard/design-guidelines/attributes)