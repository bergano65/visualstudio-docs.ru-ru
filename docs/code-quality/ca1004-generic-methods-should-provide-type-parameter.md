---
title: "CA1004: универсальные методы должны предоставлять параметр типа | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1004: универсальные методы должны предоставлять параметр типа
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Подпись параметра внешне видимого универсального метода не содержит типы, соответствующие всем параметрам типа метода.  
  
## Описание правила  
 Вывод – это то, как аргумент типа универсального метода определяется по типу аргумента, переданного методу, а не по явному указанию аргумента типа.  Чтобы задействовать вывод, сигнатура параметра универсального метода должна включать параметр, тип которого совпадает с параметром типа для метода.  В этом случае аргумент типа указывать не обязательно.  При использовании вывода для всех параметров типа синтаксис вызова универсальных и неуниверсальных методов экземпляра является одинаковым.  Это упрощает работу с универсальными методами.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, измените структуру таким образом, чтобы подпись параметра содержала одинаковый тип для каждого параметра типа метода.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Использование универсальных типов в синтаксисе, который легко понимать и использовать, сокращает время, необходимое на обучение, и улучшает скорость адаптации новых библиотек.  
  
## Пример  
 В приведенном ниже примере показан синтаксис вызова двух универсальных методов.  Аргумент типа для `InferredTypeArgument` вызван, в то время как аргумент типа для `NotInferredTypeArgument` должен быть указан явным образом.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: используйте универсальные методы, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)