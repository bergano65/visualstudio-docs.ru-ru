---
title: 'CA1039: списки обладают строгой типизацией'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dc14aca81f20a33bce5be99a2ccaf5ccad7d5b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: списки обладают строгой типизацией
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.IList?displayProperty=fullName> , но не предоставляет метод со строгой типизацией для одного или нескольких из следующих действий:

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>Описание правила
 Это правило требует <xref:System.Collections.IList> реализации предоставляли строго типизированные элементы, чтобы пользователям не придется приводить аргументы к <xref:System.Object?displayProperty=fullName> типа при использовании функциональных возможностей интерфейса. <xref:System.Collections.IList> Интерфейс реализуется классом коллекции объектов, доступных по индексу. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IList> делает это для управления коллекцией экземпляров типа, более строгого, чем <xref:System.Object>.

 <xref:System.Collections.IList> реализует <xref:System.Collections.ICollection?displayProperty=fullName> и <xref:System.Collections.IEnumerable?displayProperty=fullName> интерфейсов. Если вы реализуете <xref:System.Collections.IList>, необходимо предоставить обязательные строго типизированные члены для <xref:System.Collections.ICollection>. Если расширение объектов в коллекции <xref:System.ValueType?displayProperty=fullName>, необходимо указать строго типизированный элемент для <xref:System.Collections.IEnumerable.GetEnumerator%2A> во избежание на снижение производительности, вызванные упаковка-преобразование; это не является обязательным, если объекты коллекции имеют ссылочный тип.

 В соответствии с этим правилом текста явно реализуйте члены интерфейса с помощью имен в виде InterfaceName.InterfaceMemberName, такие как <xref:System.Collections.IList.Add%2A>. Явные члены интерфейса используйте типы данных, которые объявлены в интерфейсе. Реализовать строго типизированные элементы, используя имена членов интерфейса, такие как `Add`. Объявите строго типизированные члены как открытые и объявления параметров и возвращаемых значений иметь строгий тип, который управляется коллекции. Строгие типы заменяют слабый типы, такие как <xref:System.Object> и <xref:System.Array> , которые были объявлены в интерфейсе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, явно реализовать <xref:System.Collections.IList> членов и предоставить со строгой типизацией вместо членов, которые ранее были указаны. Для кода, который реализует правильно <xref:System.Collections.IList> интерфейсов и предоставляет требуемый строго типизированные элементы, см. следующий пример.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, при реализации новой коллекции на базе объектов, например связанного списка, где типы, расширяющие новую коллекцию, определяют строгий тип. Эти типы должны соответствовать следующему правилу и предоставлять строго типизированные члены.

## <a name="example"></a>Пример
 В следующем примере тип `YourType` расширяет <xref:System.Collections.CollectionBase?displayProperty=fullName>, как и следует всех строго типизированных коллекций. Обратите внимание, что <xref:System.Collections.CollectionBase> предоставляет явную реализацию метода <xref:System.Collections.IList> интерфейса. Таким образом, необходимо указать только строго типизированные члены для <xref:System.Collections.IList> и <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>См. также
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>