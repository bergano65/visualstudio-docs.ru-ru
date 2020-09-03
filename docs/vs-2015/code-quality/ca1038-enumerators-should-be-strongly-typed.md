---
title: 'CA1038: перечислители должны быть строго типизированы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548269"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038. Перечислители должны иметь строгие типы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует, <xref:System.Collections.IEnumerator?displayProperty=fullName> но не предоставляет строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> Свойства. Из этого правила исключены типы, производные от следующих типов:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Это правило требует, <xref:System.Collections.IEnumerator> чтобы реализации также предоставляли строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A> свойства, так что пользователям не требуется приводить возвращаемое значение к строгому типу при использовании функций, предоставляемых интерфейсом. Это правило предполагает, что тип, реализующий, <xref:System.Collections.IEnumerator> содержит коллекцию экземпляров типа, которые являются более надежными, чем <xref:System.Object> .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно реализуйте свойство интерфейса (объявите его как `IEnumerator.Current` ). Добавьте открытую строго типизированную версию свойства, объявленную как `Current` , и возвращающую строго типизированный объект.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила при реализации перечислителя на основе объектов для использования с коллекцией на основе объектов, такой как двоичное дерево. Типы, расширяющие новую коллекцию, определяют строго типизированный перечислитель и предоставляют строго типизированное свойство.

## <a name="example"></a>Пример
 В следующем примере демонстрируется правильный способ реализации строго типизированного <xref:System.Collections.IEnumerator> типа.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1035. В составе реализаций ICollection есть члены со строгим типом](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039. Списки имеют строгие типы](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также:
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
