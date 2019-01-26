---
title: CA1013. Перегружайте оператор равенства при перегрузке операторов сложения и вычитания
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 3569179148d3d1843f143571301fa18816c8dce3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041182"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013. Перегружайте оператор равенства при перегрузке операторов сложения и вычитания

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует операторы сложения или вычитания без реализации оператора равенства.

## <a name="rule-description"></a>Описание правила
 Когда экземпляры типа могут быть объединены с помощью операций, таких как сложение и вычитание, почти всегда следует определить равенство возвратит `true` для любых двух экземпляров, которые имеют те же составные значения.

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
 Чтобы устранить нарушение этого правила, реализуйте оператор равенства, чтобы он был математически совместим с операторы сложения и вычитания.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, при реализации оператора равенства по умолчанию обеспечивает правильное поведение для типа.

## <a name="example"></a>Пример
 В следующем примере определяется типом (`BadAddableType`), нарушает это правило. Этот тип должен реализовать оператор равенства, чтобы любые два экземпляра, которые имеют одинаковые значения полей тестирования `true` на предмет равенства. Тип `GoodAddableType` показана исправленная реализация. Обратите внимание, что этот тип также реализует оператор неравенства и переопределяет <xref:System.Object.Equals%2A> для выполнения других правил. Полная реализация также реализовать <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Пример
 В следующем примере проверяется на равенство с помощью экземпляров типов, которые ранее были определены в этой статье для демонстрации по умолчанию и правильное поведение для оператора равенства.

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