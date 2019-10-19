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
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661768"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: перечислители должны быть строго типизированы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.Collections.IEnumerator?displayProperty=fullName> но не предоставляет строго типизированную версию свойства <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>. Из этого правила исключены типы, производные от следующих типов:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Это правило требует, чтобы <xref:System.Collections.IEnumerator> реализации также предоставляли строго типизированную версию свойства <xref:System.Collections.IEnumerator.Current%2A>, чтобы пользователям не требовалось приводить возвращаемое значение к строгому типу при использовании функций, предоставляемых интерфейсом. Это правило предполагает, что тип, реализующий <xref:System.Collections.IEnumerator>, содержит коллекцию экземпляров типа, которая надежнее, чем <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, явно реализуйте свойство интерфейса (объявите его как `IEnumerator.Current`). Добавьте открытую строго типизированную версию свойства, объявленную как `Current` и возвращающую строго типизированный объект.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила при реализации перечислителя на основе объектов для использования с коллекцией на основе объектов, такой как двоичное дерево. Типы, расширяющие новую коллекцию, определяют строго типизированный перечислитель и предоставляют строго типизированное свойство.

## <a name="example"></a>Пример
 В следующем примере демонстрируется правильный способ реализации строго типизированного типа <xref:System.Collections.IEnumerator>.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
