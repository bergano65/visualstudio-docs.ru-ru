---
title: 'CA1039: списки строго типизированы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e485375c12564b5416c79bd3a41dedb1da76dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533449"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039. Списки имеют строгие типы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует, <xref:System.Collections.IList?displayProperty=fullName> но не предоставляет строго типизированный метод для одного или нескольких следующих элементов:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. INSERT

- IList. Remove

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.IList> реализации строго типизированных членов, чтобы пользователи не применялись для приведения аргументов к <xref:System.Object?displayProperty=fullName> типу, если они используют функциональные возможности, предоставляемые интерфейсом. <xref:System.Collections.IList>Интерфейс реализуется коллекциями объектов, к которым можно получить доступ по индексу. Это правило предполагает, что тип, реализующий <xref:System.Collections.IList> это, позволяет управлять коллекцией экземпляров типа, которые являются надежными, чем <xref:System.Object> .

 <xref:System.Collections.IList> реализует <xref:System.Collections.ICollection?displayProperty=fullName> интерфейсы и <xref:System.Collections.IEnumerable?displayProperty=fullName> . При реализации необходимо <xref:System.Collections.IList> предоставить обязательные строго типизированные члены для <xref:System.Collections.ICollection> . Если объекты в коллекции расширяются <xref:System.ValueType?displayProperty=fullName> , необходимо предоставить строго типизированный элемент, <xref:System.Collections.IEnumerable.GetEnumerator%2A> чтобы избежать снижения производительности, вызванной упаковкой-преобразованием; это не является обязательным, если объекты коллекции являются ссылочным типом.

 Чтобы обеспечить соответствие этому правилу, реализуйте члены интерфейса явным образом с помощью имен в формате InterfaceName. Интерфацемембернаме, например <xref:System.Collections.IList.Add%2A> . Явные члены интерфейса используют типы данных, объявленные интерфейсом. Реализуйте строго типизированные члены с помощью имени члена интерфейса, например `Add` . Объявите строго типизированные члены как открытые и объявите параметры и возвращаемые значения строгим типом, который управляется коллекцией. Строгие типы заменяют более слабые типы, такие как <xref:System.Object> и <xref:System.Array> , объявленные интерфейсом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно реализуйте <xref:System.Collections.IList> члены и предоставьте строго типизированные альтернативы для элементов, которые были отмечены ранее. Для кода, который правильно реализует <xref:System.Collections.IList> интерфейс и предоставляет необходимые строго типизированные члены, см. Следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила при реализации новой коллекции на основе объектов, такой как связанный список, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать этому правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере тип `YourType` расширяет <xref:System.Collections.CollectionBase?displayProperty=fullName> , как и все строго типизированные коллекции. Обратите внимание, что <xref:System.Collections.CollectionBase> предоставляет явную реализацию <xref:System.Collections.IList> интерфейса. Поэтому необходимо предоставить только строго типизированные члены для <xref:System.Collections.IList> и <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1035. В составе реализаций ICollection есть члены со строгим типом](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038. Перечислители должны иметь строгие типы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>См. также:
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
