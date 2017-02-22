---
title: "CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals | Microsoft Docs"
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
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип значения переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>,но не реализует оператор равенства.  
  
## Описание правила  
 В большинстве языков программирования для типов значений не существует реализации оператора равенства \(\=\=\) по умолчанию.  Если используемый язык программирования поддерживает перегрузки операторов, следует рассмотреть возможность реализации оператора равенства.  Его поведение должно быть идентично поведению <xref:System.Object.Equals%2A>.  
  
 Заданный по умолчанию оператор равенства нельзя использовать в перегруженной реализации оператора равенства.  Это может привести к переполнению стека.  Для реализации оператора равенства воспользуйтесь методом Object.Equals.  Примеры.  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте оператор равенства.  
  
## Отключение предупреждений  
 Для данного правила можно отключить вывод предупреждений, однако, если возможно, рекомендуется предоставить оператор равенства.  
  
## Пример  
 В следующем примере определяется тип, нарушающий это правило.  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>