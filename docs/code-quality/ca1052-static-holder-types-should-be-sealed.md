---
title: "CA1052: типы со статическими заполнителями должны быть запечатаны | Microsoft Docs"
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
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1052: типы со статическими заполнителями должны быть запечатаны
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип содержит только статические члены и не объявлен с модификатором [запечатанные](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\).  
  
## Описание правила  
 Это правило предполагает, что тип, содержащий только статические члены, не должен быть унаследованным, поскольку он не предоставляет какие\-либо функциональные возможности, которые могут быть переопределены в производном типе.  Тип, который не должен быть унаследованным, должен быть помечен модификатором `sealed`, чтобы его нельзя было использовать как базовый тип.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, пометьте тип как `sealed`.  Если целевой платформой является [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 или ранее, то лучшим вариантом будет пометить тип как `static`.  Таким образом можно избежать необходимости объявлять закрытый конструктор для предотвращения создания класса.  
  
## Отключение предупреждений  
 Отключать предупреждение из этого правила следует только в том случае, если тип должен быть наследуемым.  Отсутствие модификатора `sealed` подразумевает, что тип полезен как базовый.  
  
## Пример нарушения  
  
### Описание  
 В следующем примере показан тип, который нарушает данное правило.  
  
### Код  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Исправление с использованием статического модификатора  
  
### Описание  
 В следующем примере показано, как исправить нарушение этого правила, пометив тип модификатором `static`.  
  
### Код  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Связанные правила  
 [CA1053: типы статических владельцев не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)