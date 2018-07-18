---
title: 'CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11841248192bc9b726076641e1219f54ab526447
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897435"
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

 **Неверный тип: {2,2} {2,2} равны? Не**
**удобно: {3,3} {3,3} равны? Да**
**удобно: {3,3} {3,3} являются ==?   Да**
**неправильный тип: {2,2} {9,9} равны? Не**
**удобно: {3,3} {9,9} являются ==?   Нет**
## <a name="see-also"></a>См. также
 [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)