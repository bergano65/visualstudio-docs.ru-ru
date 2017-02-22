---
title: "CA2222: не уменьшайте видимость унаследованных членов | Microsoft Docs"
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
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2222: не уменьшайте видимость унаследованных членов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Закрытый метод в незапечатанном типе имеет подпись, идентичную с открытым методом, объявленным в базовом типе.  Закрытый метод не является окончательным.  
  
## Описание правила  
 Не следует изменять модификатор доступа для унаследованных членов.  Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен.  Если сделать член закрытым при незапечатанном типе, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования.  Чтобы изменить модификатор доступа следует либо пометить метод как окончательный, либо запечатать его тип, чтобы избежать переопределения.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, измените доступ \(он не должен быть закрытым\).  Либо можно сделать метод окончательным, если это поддерживается используемым языком программирования.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]