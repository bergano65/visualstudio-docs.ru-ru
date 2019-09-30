---
title: CA1039. Списки имеют строгие типы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcc399457f4dde1c65836d9c9498c782ba92ecc2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235992"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039. Списки имеют строгие типы

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Открытый или защищенный тип реализует <xref:System.Collections.IList?displayProperty=fullName> , но не предоставляет строго типизированный метод для одного или нескольких следующих элементов:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. INSERT

- IList. Remove

## <a name="rule-description"></a>Описание правила

Это правило требует <xref:System.Collections.IList> реализации для предоставления строго типизированных членов, поэтому пользователям не нужно приводить аргументы <xref:System.Object?displayProperty=fullName> к типу, если они используют функциональные возможности, предоставляемые интерфейсом. <xref:System.Collections.IList> Интерфейс реализуется коллекциями объектов, к которым можно получить доступ по индексу. Это правило предполагает, что тип, реализующий <xref:System.Collections.IList> , управляет коллекцией экземпляров типа, которые более надежны, чем. <xref:System.Object>

<xref:System.Collections.IList>реализует интерфейсы <xref:System.Collections.IEnumerable?displayProperty=fullName>и. <xref:System.Collections.ICollection?displayProperty=fullName> При реализации <xref:System.Collections.IList>необходимо предоставить обязательные строго типизированные члены для <xref:System.Collections.ICollection>. Если объекты в коллекции расширяются <xref:System.ValueType?displayProperty=fullName>, необходимо предоставить строго типизированный <xref:System.Collections.IEnumerable.GetEnumerator%2A> элемент, чтобы избежать снижения производительности, вызванной упаковкой-преобразованием; это не является обязательным, если объекты коллекции являются ссылочным типом.

Чтобы обеспечить соответствие этому правилу, реализуйте члены интерфейса явным образом с помощью имен в формате InterfaceName. Интерфацемембернаме, например <xref:System.Collections.IList.Add%2A>. Явные члены интерфейса используют типы данных, объявленные интерфейсом. Реализуйте строго типизированные члены с помощью имени члена интерфейса, например `Add`. Объявите строго типизированные члены как открытые и объявите параметры и возвращаемые значения строгим типом, который управляется коллекцией. Строгие типы заменяют более слабые <xref:System.Object> типы <xref:System.Array> , такие как и, объявленные интерфейсом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, явно реализуйте <xref:System.Collections.IList> члены и предоставьте строго типизированные альтернативы для элементов, которые были отмечены ранее. Для кода, который правильно реализует <xref:System.Collections.IList> интерфейс и предоставляет необходимые строго типизированные члены, см. Следующий пример.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять предупреждение из этого правила при реализации новой коллекции на основе объектов, такой как связанный список, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать этому правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
В следующем примере тип `YourType` расширяется <xref:System.Collections.CollectionBase?displayProperty=fullName>, так как все строго типизированные коллекции должны. <xref:System.Collections.CollectionBase>предоставляет явную реализацию <xref:System.Collections.IList> интерфейса. Поэтому необходимо предоставить только строго типизированные члены для <xref:System.Collections.IList> и. <xref:System.Collections.ICollection>

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1035: Реализации ICollection имеют строго типизированные члены](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Перечислители должны быть строго типизированными](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>См. также

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>