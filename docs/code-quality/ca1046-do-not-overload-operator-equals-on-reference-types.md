---
title: "CA1046: не перегружайте оператор равенства для ссылочных типов | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: не перегружайте оператор равенства для ссылочных типов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или вложенный открытый ссылочный тип перегружает оператор равенства.  
  
## Описание правила  
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов.  По умолчанию две ссылки равны, если они указывают на один объект.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите реализацию оператора равенства.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила безопасно в том случае, если ссылочный тип ведет себя как встроенный тип значения.  Бессмысленно выполнять операции сложения или вычитания для экземпляров этого типа; возможно, будет правильным реализовать оператор равенства и отключить предупреждения о нарушении.  
  
## Пример  
 В следующем примере демонстрируется поведение по умолчанию при сравнении двух ссылок.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Пример  
 В следующем приложении сравниваются несколько ссылок.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **a \= new \(2,2\) и b \= new \(2,2\) равны?  Нет**  
**c и a равны?  Да**  
**b и a \=\= ?  Нет**  
**c и a \=\= ?  Да**    
## Связанные правила  
 [CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Операторы равенства](../Topic/Equality%20Operators.md)