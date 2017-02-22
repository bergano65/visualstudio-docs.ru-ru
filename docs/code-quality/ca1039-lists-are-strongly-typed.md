---
title: "CA1039: списки обладают строгой типизацией | Microsoft Docs"
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
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1039: списки обладают строгой типизацией
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип реализует <xref:System.Collections.IList?displayProperty=fullName>, но не предоставляет метод со строгой типизацией для одного или нескольких следующих объектов:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Описание правила  
 Это правило требует, чтобы реализации <xref:System.Collections.IList> предоставляли строго типизированные члены, поскольку тогда пользователям не придется приводить аргументы к типу <xref:System.Object?displayProperty=fullName> при использовании функциональных возможностей интерфейса.  Интерфейс <xref:System.Collections.IList> реализуется коллекциями объектов, доступ к которым осуществляется посредством индекса.  В этом правиле предполагается, что тип, реализующий <xref:System.Collections.IList>, делает это для управления коллекцией экземпляров типа, более строгого, чем <xref:System.Object>.  
  
 <xref:System.Collections.IList> реализует интерфейсы <xref:System.Collections.ICollection?displayProperty=fullName> и <xref:System.Collections.IEnumerable?displayProperty=fullName>.  При реализации <xref:System.Collections.IList> нужно предоставить необходимые члены со строгой типизацией для <xref:System.Collections.ICollection>.  Если объекты в коллекции расширяют <xref:System.ValueType?displayProperty=fullName>, нужно предоставить член со строгой типизацией для <xref:System.Collections.IEnumerable.GetEnumerator%2A>, чтобы избежать снижения производительности, вызванной упаковкой. Этого не требуется, если объекты коллекции являются ссылочным типом.  
  
 Для выполнения этого правила реализуйте члены интерфейса явным образом, используя имена в форме имя\_интерфейса.имя\_члена\_интерфейса, например <xref:System.Collections.IList.Add%2A>.  Явно реализованные члены интерфейса используют типы данных, объявленные в интерфейсе.  Типобезопасные члены следует реализовывать, используя имена членов интерфейса, например `Add`.  Объявите типобезопасные члены как открытые, а параметры и возвращаемые значения объявите принадлежащими строгому типу, управляемому коллекцией.  Строгие типы заменяют более слабые типы, такие как <xref:System.Object> и <xref:System.Array>, объявленные в интерфейсе.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, следует явным образом реализовать члены <xref:System.Collections.IList> и обеспечить альтернативные члены со строгой типизацией вместо указанных ранее членов.  Пример кода с правильной реализацией интерфейса <xref:System.Collections.IList> и с необходимыми элементами со строгой типизацией см. ниже.  
  
## Отключение предупреждений  
 Предупреждения этого правила следует отключать при реализации новой коллекции на базе объектов, например связанного списка, где типы, расширяющие новую коллекцию, определяют строгий тип.  Эти типы должны удовлетворять данному правилу и предоставлять типобезопасные члены.  
  
## Пример  
 В следующем примере тип `YourType` расширяет <xref:System.Collections.CollectionBase?displayProperty=fullName>, как должны делать все коллекции со строгой типизацией.  Обратите внимание, что <xref:System.Collections.CollectionBase> предоставляет явную реализацию интерфейс <xref:System.Collections.IList>.  Таким образом, необходимо только указать строго типизированные члены для <xref:System.Collections.IList> и <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Связанные правила  
 [CA1035: в составе реализаций ICollection есть строго типизированные элементы](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## См. также  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>