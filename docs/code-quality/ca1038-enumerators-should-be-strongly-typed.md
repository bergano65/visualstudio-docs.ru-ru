---
title: "CA1038: Перечислители должны быть строго типизированы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c08d8ce661e46f76da6d2880bd6b4e833f0b4d1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: перечислители должны быть строго типизированы
|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип реализует <xref:System.Collections.IEnumerator?displayProperty=fullName> , но не предоставляет строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> свойство. Типы, которые являются производными от следующих типов будут исключены из этого правила:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>Описание правила  
 Это правило требует <xref:System.Collections.IEnumerator> реализации предоставляли строго типизированную версию <xref:System.Collections.IEnumerator.Current%2A> свойство, чтобы пользователям не придется приводить возвращаемое значение к строгому типу при использовании функциональных возможностей интерфейса. В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IEnumerator> содержит коллекцию экземпляров типа, более строгого, чем <xref:System.Object>.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализовать свойство интерфейса явно (он объявляется как `IEnumerator.Current`). Добавьте открытый строго типизированную версию свойства, объявленные как `Current`, и вернуть строго типизированный объект, его.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, при реализации перечислитель на основе объекта для использования с коллекцией объектов, например двоичного дерева. Типы, расширяющие новую коллекцию определит перечислитель со строгой типизацией и предоставят строго типизированное свойство.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует правильный способ реализации со строгой типизацией <xref:System.Collections.IEnumerator> типа.  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>