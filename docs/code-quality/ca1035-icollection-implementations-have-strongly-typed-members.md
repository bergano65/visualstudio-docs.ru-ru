---
title: "CA1035: в составе реализаций ICollection есть строго типизированные элементы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035: в составе реализаций ICollection есть строго типизированные элементы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип реализует интерфейс <xref:System.Collections.ICollection?displayProperty=fullName>, однако не предоставляет типобезопасный метод для <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>.  Типобезопасная версия метода <xref:System.Collections.ICollection.CopyTo%2A> должна принимать два параметра и не может содержать в качестве первого параметра объект <xref:System.Array?displayProperty=fullName> или массив объектов <xref:System.Object?displayProperty=fullName>.  
  
## Описание правила  
 Это правило требует, чтобы реализации <xref:System.Collections.ICollection> предоставляли строго типизированные члены, поскольку тогда пользователям не придется приводить аргументы к типу <xref:System.Object> при использовании функциональных возможностей интерфейса.  В данном правиле предполагается, что тип реализует интерфейс <xref:System.Collections.ICollection> для управления коллекцией экземпляров более строгого типа, чем <xref:System.Object>.  
  
 Интерфейс <xref:System.Collections.ICollection> реализует интерфейс <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Если объекты в коллекции расширяют <xref:System.ValueType?displayProperty=fullName>, нужно предоставить член со строгой типизацией для <xref:System.Collections.IEnumerable.GetEnumerator%2A>, чтобы избежать снижения производительности, вызванной упаковкой.  Это не требуется, если объекты коллекции имеют ссылочный тип.  
  
 Чтобы реализовать строго типизированную версию члена интерфейса, следует явно реализовать члены интерфейса, используя имена в форме `InterfaceName.InterfaceMemberName`, например <xref:System.Collections.ICollection.CopyTo%2A>.  Явно реализованные члены интерфейса используют типы данных, объявленные в интерфейсе.  Типобезопасные члены следует реализовывать, используя имена членов интерфейса, например <xref:System.Collections.ICollection.CopyTo%2A>.  Объявите типобезопасные члены как открытые, а параметры и возвращаемые значения объявите принадлежащими строгому типу, управляемому коллекцией.  Строгие типы заменяют более слабые типы, такие как <xref:System.Object> и <xref:System.Array>, объявленные в интерфейсе.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, явно реализуйте член интерфейса \(объявите его как <xref:System.Collections.ICollection.CopyTo%2A>\).  Добавьте открытый типобезопасный член, объявленный как `CopyTo`, и укажите в качестве его первого параметра типобезопасный массив.  
  
## Отключение предупреждений  
 Отключите предупреждения о нарушении данного правила при реализации новой коллекции на базе объектов, например двоичного дерева, в котором типы, расширяющие новую коллекцию, определяют строгий тип.  Эти типы должны удовлетворять данному правилу и предоставлять типобезопасные члены.  
  
## Пример  
 В следующем примере демонстрируется правильный способ реализации интерфейса <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Связанные правила  
 [CA1038: перечислители должны быть строго типизированы](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: списки обладают строгой типизацией](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## См. также  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>