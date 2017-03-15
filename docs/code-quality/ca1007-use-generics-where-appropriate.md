---
title: "CA1007: используйте универсальные методы, если это уместно | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1007: используйте универсальные методы, если это уместно
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый для внешнего кода метод содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName>, однако сборка, в которой он находится, предназначена для среды [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Описание правила  
 Ссылочный параметр — это параметр, измененный с помощью ключевого слова `ref` \(`ByRef` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Тип аргумента, передаваемого для ссылочного параметра, должен точно совпадать с типом ссылочного параметра.  Чтобы использовать тип, производный от типа ссылочного параметра, тип необходимо сначала привести и присвоить переменной типа ссылочного параметра.  Использование универсального метода позволяет передавать в метод все типы без предварительного приведения к типу ссылочного параметра при условии выполнения некоторых ограничений.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте метод универсальным и замените параметр <xref:System.Object> параметром типа.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показана процедура замены общего назначения, реализованная посредством как универсального, так и неуниверсального метода.  Обратите внимание, что с помощью универсального метода строки заменяются гораздо эффективнее, чем при помощи неуниверсального метода.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)