---
title: "CA1005: не используйте слишком много параметров в универсальных типах | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1005: не используйте слишком много параметров в универсальных типах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Внешне видимый универсальный тип имеет более двух параметров типов.  
  
## Описание правила  
 Чем больше параметров типов содержит универсальный тип, тем сложнее знать и запоминать, что представляет каждый параметр типа.  Это обычно становится очевидным при одном параметре типа, как в `List<T>`, и в ряде случаев при двух параметрах типов, как в `Dictionary<TKey, TValue>`.  Если используется более двух параметров типов, большинство пользователей начинают испытывать большие трудности \(например, `TooManyTypeParameters<T, K, V>` в C\# или `TooManyTypeParameters(Of T, K, V)` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, не используйте при разработке более двух параметров типов.  
  
## Отключение предупреждений  
 Не следует отключать предупреждение из этого правила, если просто необходимо использовать более двух параметров типов.  Использование универсальных типов в синтаксисе, который легко понимать и использовать, сокращает время, необходимое на обучение, и улучшает скорость адаптации новых библиотек.  
  
## Связанные правила  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: используйте универсальные методы, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)