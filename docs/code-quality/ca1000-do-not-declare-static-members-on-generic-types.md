---
title: "CA1000: не объявляйте статические элементы в универсальных типах | Microsoft Docs"
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
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1000: не объявляйте статические элементы в универсальных типах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый снаружи универсальный тип содержит элемент с модификатором `static` \(`Shared` в Visual Basic\).  
  
## Описание правила  
 При вызове метода универсального типа с модификатором `static` для типа нужно указать аргумент типа.  При вызове универсального экземпляра элемента, не поддерживающего вывод типа, для элемента нужно указать аргумент типа.  Синтаксис для аргумента типа различается в этих двух случаях, его легко перепутать, как показано в следующих вызовах:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 В общем случае следует избегать заблаговременного объявления, чтобы не при вызове элемента не требовалось указывать аргумент типа.  В результате синтаксис вызова элемента для универсальных типов не будет отличаться от синтаксиса для неуниверсальных типов.  Для получения дополнительной информации см. [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалите статический элемент или измените его, сделав его элементов экземпляра.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Использование универсальных типов в синтаксисе, который легко понимать и использовать, сокращает время, необходимое на обучение, и улучшает скорость адаптации новых библиотек.  
  
## Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: используйте универсальные методы, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)