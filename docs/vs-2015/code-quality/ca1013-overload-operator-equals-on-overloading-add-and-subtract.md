---
title: 'CA1013: перегрузка оператора Equals при перегрузке Add и Subtract | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1c144f04150e3965e2c0264b80147cbd9b8f19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663202"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует операторы сложения или вычитания без реализации оператора равенства.

## <a name="rule-description"></a>Описание правила
 Если экземпляры типа можно комбинировать с помощью таких операций, как сложение и вычитание, почти всегда следует определять равенство для возврата `true` для всех двух экземпляров, имеющих одинаковые составные значения.

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

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если реализация оператора равенства по умолчанию обеспечивает правильное поведение для типа.

## <a name="example"></a>Пример
 В следующем примере определяется тип (`BadAddableType`), нарушающий это правило. Этот тип должен реализовать оператор равенства, чтобы два экземпляра с одинаковыми значениями полей протестировать `true` на равенство. В `GoodAddableType` типа показана исправленная реализация. Обратите внимание, что этот тип также реализует оператор неравенства и переопределяет <xref:System.Object.Equals%2A> для удовлетворения других правил. Полная реализация также будет реализовывать <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Пример
 В следующем примере проверяется равенство с помощью экземпляров типов, которые ранее были определены в этом разделе, чтобы проиллюстрировать поведение по умолчанию и правильно использовать оператор равенства.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 В этом примере формируются следующие данные:

 **Неверный тип: {2,2} {2,2} равны? Нет** 
**хорошего типа: {3,3} {3,3} равны? Да** 
**хороший тип: {3,3} 0 = =?   Да** 1**неверный тип: 3 4 равны? Нет** 5**правильного типа: 7 8 = =?   Нет**
## <a name="see-also"></a>См. также раздел
 [Операторы равенства](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
