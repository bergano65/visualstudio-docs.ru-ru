---
title: "CA1048: не объявляйте виртуальные элементы в запечатанных типах | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1048: не объявляйте виртуальные элементы в запечатанных типах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый тип является запечатанным и объявляет метод, обладающий свойством `virtual` \(`Overridable` в Visual Basic\) и не являющийся окончательным.  Это правило не касается нарушений типов делегатов, в которых такой шаблон обязателен.  
  
## Описание правила  
 Типы объявляют методы как виртуальные, чтобы наследующие типы могли переопределять реализацию виртуального метода.  По определению невозможно наследовать от запечатанного типа, поэтому объявлять виртуальные метода в запечатанном типе не имеет смысла.  
  
 Компиляторы Visual Basic .NET и C\# запрещают нарушение этого правила типами.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, сделайте метод невиртуальным или сделайте тип ненаследуемым.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Если оставить тип в текущем состоянии, могут возникнуть проблемы обслуживания, а никаких преимуществ это не даст.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]