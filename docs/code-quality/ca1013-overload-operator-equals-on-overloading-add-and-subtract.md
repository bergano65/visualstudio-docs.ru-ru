---
title: "CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый или защищенный тип реализует операторы сложения или вычитания без реализации оператора равенства.  
  
## Описание правила  
 Если экземпляры типа можно сочетать при помощи таких операций как сложение и вычитание, нужно почти всегда определять операцию равенства, которая должна возвращать значение `true` для любых двух экземпляров с одинаковыми составляющими значениями.  
  
 Заданный по умолчанию оператор равенства нельзя использовать в перегруженной реализации оператора равенства.  Это может привести к переполнению стека.  Для реализации оператора равенства воспользуйтесь методом Object.Equals.  См. следующий пример.  
  
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
 Чтобы исправить нарушение этого правила, реализуйте оператор равенства, чтобы он был математически однородным с операторами сложения и вычитания.  
  
## Отключение предупреждений  
 Можно безопасно отключать предупреждения этого правила, если заданная по умолчанию реализация оператора равенства обеспечивает его правильную работу для заданного типа.  
  
## Пример  
 В следующем примере определяется тип \(`BadAddableType`\), нарушающий это правило.  Этот тип должен реализовать оператор равенства, чтобы любые два экземпляра с одинаковыми значениями полей выдавали значение `true` для равенства.  Тип `GoodAddableType` демонстрирует исправленную реализацию.  Обратите внимание, что этот тип также реализует оператор неравенства и переопределяет <xref:System.Object.Equals%2A> для выполнения других правил.  При полной реализации также потребуется реализовать <xref:System.Object.GetHashCode%2A>.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Пример  
 В следующем примере проверяется равенство с помощью экземпляров типов, которые были определены раннее в этом разделе, для демонстрации правильного поведения оператора равенства.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **Неверный тип:  {2,2} {2,2} равны?  Нет**  
**Верный тип: {3,3} {3,3} равны?  Да**  
**Верный тип: {3,3} {3,3} \=\= ?   Да**  
**Неверный тип:  {2,2} {9,9} равны?  Нет**  
**Верный тип: {3,3} {9,9} \=\= ?   Нет**    
## См. также  
 [Операторы равенства](../Topic/Equality%20Operators.md)