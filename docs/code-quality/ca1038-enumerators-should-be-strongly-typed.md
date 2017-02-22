---
title: "CA1038: перечислители должны быть строго типизированы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038: перечислители должны быть строго типизированы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип реализует <xref:System.Collections.IEnumerator?displayProperty=fullName>, но не предоставляет версию свойства <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> со строгой типизацией.  Это правило не касается типов, производных от следующих типов:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Описание правила  
 Это правило требует, чтобы реализации <xref:System.Collections.IEnumerator> также предоставляли версии свойства <xref:System.Collections.IEnumerator.Current%2A> со строгой типизацией, чтобы пользователям не требовалось приводить возвращаемое значение к строгому типу при использовании функциональных возможностей интерфейса.  В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IEnumerator>, содержит коллекцию экземпляров типа, более строгого по сравнению с <xref:System.Object>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, следует явным образом реализовать свойство интерфейса \(объявить его как `IEnumerator.Current`\).  Добавьте версию свойства со строгой типизацией, объявите ее как `Current`, чтобы она возвращала объект со строгой типизацией.  
  
## Отключение предупреждений  
 Предупреждения этого правила следует отключать при реализации перечислителя на основе объектов для использования в коллекции на основе объектов, например в двоичном дереве.  Типы, расширяющие новую коллекцию, определят перечислитель со строгой типизацией и предоставят типобезопасное свойство.  
  
## Пример  
 В следующем примере показан правильный способ реализации типа <xref:System.Collections.IEnumerator> со строгой типизацией.  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## Связанные правила  
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## См. также  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>