---
title: "CA1006: не вкладывайте универсальные типы в сигнатуры членов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006: не вкладывайте универсальные типы в сигнатуры членов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Подпись видимого для внешнего кода члена содержит аргумент вложенного типа.  
  
## Описание правила  
 Аргумент вложенного типа также является аргументом универсального типа.  Чтобы вызвать член, сигнатура которого содержит аргумент вложенного типа, пользователь должен создать экземпляр одного универсального типа и передать этот тип конструктору второго универсального типа.  Это приводит к усложнению процедуры и синтаксиса, чего следует избегать.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените структуру члена, чтобы удалить аргумент вложенного типа.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Использование универсальных типов в синтаксисе, который легко понимать и использовать, сокращает время, необходимое на обучение, и улучшает скорость адаптации новых библиотек.  
  
## Пример  
 В следующем примере показан метод, который нарушает данное правило, и синтаксис, необходимый для вызова этого метода.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: используйте универсальные методы, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)