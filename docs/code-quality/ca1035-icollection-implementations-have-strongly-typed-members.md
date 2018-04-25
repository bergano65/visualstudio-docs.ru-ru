---
title: 'CA1035: в составе реализаций ICollection есть строго типизированные элементы'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40a81ea09c672728445ee4e25f82adecaa42ae79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: в составе реализаций ICollection есть строго типизированные элементы
|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.ICollection?displayProperty=fullName> , но не предоставляет строго типизированный метод для <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Строго типизированную версию <xref:System.Collections.ICollection.CopyTo%2A> должен принимать два параметра и не может иметь <xref:System.Array?displayProperty=fullName> или массив <xref:System.Object?displayProperty=fullName> первым параметром.

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.ICollection> реализации предоставляли строго типизированные элементы, чтобы пользователям не придется приводить аргументы к <xref:System.Object> типа при использовании функциональных возможностей интерфейса. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.ICollection> выполняет таким образом, для управления коллекцией экземпляров типа, более строгого, чем <xref:System.Object>.

 Класс <xref:System.Collections.ICollection> реализует интерфейс списка <xref:System.Collections.IEnumerable?displayProperty=fullName>. Если расширение объектов в коллекции <xref:System.ValueType?displayProperty=fullName>, необходимо указать строго типизированный элемент для <xref:System.Collections.IEnumerable.GetEnumerator%2A> во избежание на снижение производительности, вызванное упаковки-преобразования. Это не требуется, если объекты коллекции имеют ссылочный тип.

 Для реализации члена интерфейса строго типизированную версию, текста явно реализуйте члены интерфейса с помощью имен в виде `InterfaceName.InterfaceMemberName`, такие как <xref:System.Collections.ICollection.CopyTo%2A>. Явные члены интерфейса используйте типы данных, которые объявлены в интерфейсе. Реализовать строго типизированные элементы, используя имена членов интерфейса, такие как <xref:System.Collections.ICollection.CopyTo%2A>. Объявите строго типизированные члены как открытые и объявления параметров и возвращаемых значений иметь строгий тип, который управляется коллекции. Строгие типы заменяют слабый типы, такие как <xref:System.Object> и <xref:System.Array> , которые были объявлены в интерфейсе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, реализовать член интерфейса явно (он объявляется как <xref:System.Collections.ICollection.CopyTo%2A>). Добавьте открытый строго типизированный член, объявленный как `CopyTo`, и его в качестве первого параметра строго типизированный массив.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, при реализации новой коллекции на базе объектов, например двоичное дерево, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать следующему правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере показано, как правильно реализовать <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>