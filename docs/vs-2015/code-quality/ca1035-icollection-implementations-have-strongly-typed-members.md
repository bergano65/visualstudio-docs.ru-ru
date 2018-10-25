---
title: 'CA1035: Реализаций ICollection есть строго типизированные элементы | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c5a20352b92c5cf4089029d9b613fdf8a83a8c2e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930158"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: в составе реализаций ICollection есть строго типизированные элементы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.ICollection?displayProperty=fullName> , но не предоставляет строго типизированный метод для <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Строго типизированную версию <xref:System.Collections.ICollection.CopyTo%2A> должен принимать два параметра и не может иметь <xref:System.Array?displayProperty=fullName> или массив <xref:System.Object?displayProperty=fullName> как свой первый параметр.

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.ICollection> реализации предоставляли строго типизированные элементы, чтобы пользователям не придется приводить аргументы к <xref:System.Object> введите при использовании функциональных возможностей интерфейса. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.ICollection> делает, поэтому для управления коллекцией экземпляров типа, которое строже, чем <xref:System.Object>.

 Класс <xref:System.Collections.ICollection> реализует интерфейс списка <xref:System.Collections.IEnumerable?displayProperty=fullName>. Если расширение объектов в коллекции <xref:System.ValueType?displayProperty=fullName>, необходимо предоставить строго типизированный элемент для <xref:System.Collections.IEnumerable.GetEnumerator%2A> во избежание снижение производительности, вызванное упаковки-преобразования. Это не требуется, если объекты коллекции имеют ссылочный тип.

 Чтобы реализовать строго типизированную версию член интерфейса, реализовать члены интерфейса явно с помощью имен в виде `InterfaceName.InterfaceMemberName`, такие как <xref:System.Collections.ICollection.CopyTo%2A>. К явным членам интерфейса используйте типы данных, которые объявлены в интерфейсе. Реализовать строго типизированные элементы, используя имена членов интерфейса, такие как <xref:System.Collections.ICollection.CopyTo%2A>. Объявите строго типизированные члены как открытые и объявления параметров и возвращаемых значений строгого типа, который управляется в коллекции. Строгие типы замените слабый типы, такие как <xref:System.Object> и <xref:System.Array> , объявленные в интерфейсе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализовать член интерфейса, явным образом (он объявляется как <xref:System.Collections.ICollection.CopyTo%2A>). Добавьте открытый строго типизированный член, объявленный как `CopyTo`, и в качестве ее первый параметр строго типизированный массив.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если вы реализуете новую коллекцию на базе объектов, например двоичное дерево, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствуют данному правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере показано, как правильно реализовать <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>



