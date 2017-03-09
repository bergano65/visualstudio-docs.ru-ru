---
title: "CA1036: переопределяйте методы в сравнимых типах | Microsoft Docs"
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
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: переопределяйте методы в сравнимых типах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый или защищенный тип реализует интерфейс <xref:System.IComparable?displayProperty=fullName> и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает характерный для языка оператор равенства, неравенства, большинства или меньшинства.  Если тип только наследует реализацию интерфейса, правило не выводит сообщение о нарушении.  
  
## Описание правила  
 Типы, определяющие пользовательский порядок сортировки, реализуют интерфейс <xref:System.IComparable>.  Метод <xref:System.IComparable.CompareTo%2A> возвращает целочисленное значение, указывающее правильный порядок сортировки для двух экземпляров типа.  Это правило определяет типы, задающие порядок сортировки; это подразумевает, что обычное понимание равенства, неравенства, большинства или меньшинства не применяется.  При предоставлении реализации <xref:System.IComparable> обычно необходимо переопределить <xref:System.Object.Equals%2A> для возвращения значений, согласованных с методом <xref:System.IComparable.CompareTo%2A>.  При переопределении <xref:System.Object.Equals%2A> и кодировании на языке, поддерживающем перегрузки операторов, необходимо также предоставить операторы, согласующиеся с <xref:System.Object.Equals%2A>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, переопределите <xref:System.Object.Equals%2A>.  Если используемый язык программирования поддерживает перегрузку операторов, предоставьте следующие операторы.  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 В C\# для представления этих операторов используются следующие маркеры: \=\=, \!\=, \<, and \>.  
  
## Отключение предупреждений  
 Если причиной нарушения является отсутствие операторов и язык программирования не поддерживает перегрузку операторов \(как в случае с Visual Basic .NET\) для данного правила вывод предупреждения можно отключить.  Безопасно отключить предупреждения о нарушении данного правила при срабатывании на операторы равенства, кроме op\_Equality, если вы определили, что в реализации операторов нет смысла в контексте вашего приложения.  Тем не менее, следует всегда закрывать op\_Equality и оператор \=\= при переопределении Object.Equals.  
  
## Пример  
 В следующем примере содержится тип, правильно реализующий <xref:System.IComparable>.  Комментарии кода выявляют методы, удовлетворяющие различным правилам, связанным с <xref:System.Object.Equals%2A> и интерфейсом <xref:System.IComparable>.  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Пример  
 В следующем приложении тестируется поведение реализации <xref:System.IComparable>, представленной ранее.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## См. также  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Операторы равенства](../Topic/Equality%20Operators.md)