---
title: CA1035. В составе реализаций ICollection есть члены со строгим типом
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922830"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035. В составе реализаций ICollection есть члены со строгим типом

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Открытый или защищенный тип реализует <xref:System.Collections.ICollection?displayProperty=fullName> , но не предоставляет строго типизированный метод для <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Строго типизированная версия <xref:System.Collections.ICollection.CopyTo%2A> должна принимать два параметра и не может <xref:System.Array?displayProperty=fullName> иметь массив <xref:System.Object?displayProperty=fullName> или в качестве первого параметра.

## <a name="rule-description"></a>Описание правила
Это правило требует <xref:System.Collections.ICollection> реализации строго типизированных членов, чтобы пользователи не применялись для приведения аргументов <xref:System.Object> к типу, если они используют функциональные возможности, предоставляемые интерфейсом. Это правило предполагает, что тип, реализующий <xref:System.Collections.ICollection> , делает это для управления коллекцией экземпляров типа, которые являются более надежными, чем. <xref:System.Object>

 Класс <xref:System.Collections.ICollection> реализует интерфейс списка <xref:System.Collections.IEnumerable?displayProperty=fullName>. Если объекты в коллекции расширяются <xref:System.ValueType?displayProperty=fullName>, необходимо предоставить строго типизированный <xref:System.Collections.IEnumerable.GetEnumerator%2A> элемент, чтобы избежать снижения производительности, вызванной упаковкой-преобразованием. Это необязательно, если объекты коллекции являются ссылочным типом.

Чтобы реализовать строго типизированную версию члена интерфейса, реализуйте члены интерфейса явным образом с помощью имен в форме `InterfaceName.InterfaceMemberName`, <xref:System.Collections.ICollection.CopyTo%2A>например. Явные члены интерфейса используют типы данных, объявленные интерфейсом. Реализуйте строго типизированные члены с помощью имени члена интерфейса, например <xref:System.Collections.ICollection.CopyTo%2A>. Объявите строго типизированные члены как открытые и объявите параметры и возвращаемые значения строгим типом, который управляется коллекцией. Строгие типы заменяют более слабые <xref:System.Object> типы <xref:System.Array> , такие как и, объявленные интерфейсом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, реализуйте член интерфейса явным образом (объявите его как <xref:System.Collections.ICollection.CopyTo%2A>). Добавьте открытый строго типизированный член, объявленный `CopyTo`как, и получите строго типизированный массив в качестве своего первого параметра.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять предупреждение из этого правила, если реализуется новая коллекция на основе объектов, например двоичное дерево, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать этому правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
В следующем примере демонстрируется правильный способ реализации <xref:System.Collections.ICollection>.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1038: Перечислители должны быть строго типизированными](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Списки являются строго типизированными](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>