---
title: "CA1010: коллекции должны реализовывать универсальный интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010: коллекции должны реализовывать универсальный интерфейс
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Доступный для внешнего кода тип реализует интерфейс <xref:System.Collections.IEnumerable?displayProperty=fullName>, однако не реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> и содержащие его конечные объекты сборки платформы [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  Данное правило пропускает типы, которые реализуют интерфейс <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## Описание правила  
 Чтобы расширить возможности использования коллекции, реализуйте один из универсальных интерфейсов коллекции.  Затем данную коллекцию можно использовать для заполнения универсальных типов коллекции, например следующих:  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте один из следующих универсальных интерфейсов:  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила безопасно; однако возможности использования коллекции будут ограничены.  
  
## Пример нарушения  
  
### Описание  
 В следующем примере показан класс \(ссылочный тип\), который, в нарушение данного правила, наследует от неуниверсального класса `CollectionBase`.  
  
### Код  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Комментарии  
 Чтобы устранить нарушения в данном примере, необходимо либо реализовать универсальные интерфейсы, либо заменить базовый класс на тип, который реализует как универсальные, так и неуниверсальные интерфейсы, например класс `Collection<T>`.  
  
## Исправление посредством замены базового класса  
  
### Описание  
 В следующем примере нарушение устраняется посредством замены неуниверсального базового класса коллекции `CollectionBase` на универсальный класс `Collection<T>` \(`Collection(Of T)` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Код  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Комментарии  
 Замена базового класса уже выпущенного класса является для существующих пользователей критическим изменением.  
  
## Исправление посредством реализации интерфейсов  
  
### Описание  
 В следующем примере нарушение устраняется посредством реализации следующих универсальных интерфейсов: `IEnumerable<T>`, `ICollection<T>` и `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)` и `IList(Of T)` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Код  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: используйте универсальные методы, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)