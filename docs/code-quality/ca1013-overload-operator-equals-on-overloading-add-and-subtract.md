---
title: "CA1013: Перегружайте оператор равенства при перегрузке сложения и вычитания | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d668760159af34e8f22a69bed41de185fa4254e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип реализует операторы сложения или вычитания без реализации оператора равенства.  
  
## <a name="rule-description"></a>Описание правила  
 Когда экземпляров типа могут быть объединены с помощью операции, такие как сложение и вычитание, почти всегда следует определить равенство возвратит `true` для любых двух экземпляров, которые имеют одинаковые значения, составляющие.  
  
 Оператор проверки на равенство по умолчанию нельзя использовать в перегруженной реализации оператора равенства. Это приведет к переполнению стека. Чтобы реализовать оператор равенства, используйте метод Object.Equals в реализации. См. следующий пример.  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте оператор равенства, чтобы он был математически совместим с операторы сложения и вычитания.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если реализация оператора равенства по умолчанию обеспечивает правильное поведение для типа.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется тип (`BadAddableType`), приводит к нарушению данного правила. Этот тип должен реализовать оператор равенства, чтобы любые два экземпляра, имеющие одинаковые значения полей тестирования `true` на равенство. Тип `GoodAddableType` приведен исправленный реализации. Обратите внимание, что этот тип также реализует оператор неравенства и переопределяет <xref:System.Object.Equals%2A> для выполнения других правил. Может также реализовать полную реализацию <xref:System.Object.GetHashCode%2A>.  
  
 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере проверка на равенство с помощью экземпляров типов, которые ранее были определены в этом разделе иллюстрируют оператора равенства по умолчанию и правильное поведение.  
  
 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **Неверный тип: {2,2} {2,2} равны? Нет**  
**Тип хорошо: {3,3} {3,3} равны? Да**  
**Тип хорошо: {3,3} {3,3} являются ==?   Да**  
**Неверный тип: {2,2} {9,9} равны? Нет**  
**Тип хорошо: {3,3} {9,9} являются ==?   Нет**   
## <a name="see-also"></a>См. также  
 [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)