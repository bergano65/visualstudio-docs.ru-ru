---
title: "CA2218: переопределяйте GetHashCode при переопределении Equals | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: переопределяйте GetHashCode при переопределении Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый тип переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>, но не переопределяет <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Описание правила  
 <xref:System.Object.GetHashCode%2A> возвращает значение на основе текущего экземпляра, используемое для алгоритмов хэширования и структур данных, таких как таблица хэша.  Два равных друг другу объекта одинакового типа должны возвращать одинаковый код хэша, чтобы экземпляры следующих типов правильно работали:  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Типы, реализующие <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, предоставьте реализацию <xref:System.Object.GetHashCode%2A>.  Для пары объектов одинакового типа реализация должна возвращать одинаковое значение, если реализация <xref:System.Object.Equals%2A> возвращает `true` для этой пары.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример класса  
  
### Описание  
 В следующем примере демонстрируется класс \(ссылочный тип\), нарушающий это правило.  
  
### Код  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Комментарии  
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.GetHashCode>.  
  
### Код  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## Пример структуры  
  
### Описание  
 В следующем примере показана структура \(тип значения\), нарушающая это правило.  
  
### Код  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### Комментарии  
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.GetHashCode>.  
  
### Код  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Операторы равенства](../Topic/Equality%20Operators.md)