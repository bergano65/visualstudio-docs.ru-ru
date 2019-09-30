---
title: CA1013. Перегружайте оператор равенства при перегрузке операторов сложения и вычитания
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2bb5fd5c0e68b5dcffc212af03294d94d04d2abe
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236337"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013. Перегружайте оператор равенства при перегрузке операторов сложения и вычитания

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Открытый или защищенный тип реализует операторы сложения или вычитания без реализации оператора равенства.

## <a name="rule-description"></a>Описание правила
Если экземпляры типа можно комбинировать с помощью таких операций, как сложение и вычитание, почти всегда следует определять равенство, возвращаемое `true` для двух экземпляров, имеющих одинаковые составные значения.

Нельзя использовать оператор равенства по умолчанию в перегруженной реализации оператора равенства. Это приведет к переполнению стека. Чтобы реализовать оператор равенства, используйте метод Object. Equals в реализации. См. следующий пример.

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
Чтобы устранить нарушение этого правила, реализуйте оператор равенства, чтобы он был математически согласованным с операторами сложения и вычитания.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если реализация оператора равенства по умолчанию обеспечивает правильное поведение для типа.

## <a name="example"></a>Пример
В следующем примере определяется тип (`BadAddableType`), нарушающий это правило. Этот тип должен реализовывать оператор равенства, чтобы создать два экземпляра с одинаковыми значениями полей для проверки `true` на равенство. Тип `GoodAddableType` показывает исправленную реализацию. Обратите внимание, что этот тип также реализует оператор неравенства и <xref:System.Object.Equals%2A> переопределения для удовлетворения других правил. Полная реализация также будет реализовывать <xref:System.Object.GetHashCode%2A>.

[!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Пример
В следующем примере проверяется равенство с помощью экземпляров типов, которые ранее были определены в этом разделе, чтобы проиллюстрировать поведение по умолчанию и правильно использовать оператор равенства.

[!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

В этом примере выводятся следующие данные:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>См. также

- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)