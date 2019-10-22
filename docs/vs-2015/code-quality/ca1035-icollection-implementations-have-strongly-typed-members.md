---
title: 'CA1035: реализации ICollection имеют строго типизированные члены | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d112e2dfb704a785db6bbc5becd2b369d90605b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661844"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: в составе реализаций ICollection есть строго типизированные элементы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.ICollection?displayProperty=fullName> но не предоставляет строго типизированный метод для <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Строго типизированная версия <xref:System.Collections.ICollection.CopyTo%2A> должна принимать два параметра и не может иметь <xref:System.Array?displayProperty=fullName> или массив <xref:System.Object?displayProperty=fullName> в качестве первого параметра.

## <a name="rule-description"></a>Описание правила
 Это правило требует, чтобы <xref:System.Collections.ICollection> реализации предоставляли строго типизированные члены, чтобы пользователям не приводить аргументы к типу <xref:System.Object> при использовании функций, предоставляемых интерфейсом. Это правило предполагает, что тип, реализующий <xref:System.Collections.ICollection>, делает это для управления коллекцией экземпляров типа, которые надежнее, чем <xref:System.Object>.

 Класс <xref:System.Collections.ICollection> реализует интерфейс списка <xref:System.Collections.IEnumerable?displayProperty=fullName>. Если объекты в коллекции расширяют <xref:System.ValueType?displayProperty=fullName>, необходимо предоставить строго типизированный элемент для <xref:System.Collections.IEnumerable.GetEnumerator%2A>, чтобы избежать снижения производительности, вызванного упаковкой. Это необязательно, если объекты коллекции являются ссылочным типом.

 Чтобы реализовать строго типизированную версию члена интерфейса, реализуйте члены интерфейса явным образом, используя имена в форме `InterfaceName.InterfaceMemberName`, например <xref:System.Collections.ICollection.CopyTo%2A>. Явные члены интерфейса используют типы данных, объявленные интерфейсом. Реализуйте строго типизированные члены, используя имя члена интерфейса, например <xref:System.Collections.ICollection.CopyTo%2A>. Объявите строго типизированные члены как открытые и объявите параметры и возвращаемые значения строгим типом, который управляется коллекцией. Строгие типы заменяют более слабые типы, такие как <xref:System.Object> и <xref:System.Array>, объявленные интерфейсом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно реализуйте член интерфейса (объявите его как <xref:System.Collections.ICollection.CopyTo%2A>). Добавьте открытый строго типизированный член, объявленный как `CopyTo`, и получите строго типизированный массив в качестве своего первого параметра.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если реализуется новая коллекция на основе объектов, например двоичное дерево, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать этому правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере демонстрируется правильный способ реализации <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
