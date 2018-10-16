---
title: 'CA1013: Перегружайте оператор равенства при перегрузке Добавление и вычитание | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ad1213ad0f24ef3e98a7311719fbff4dc7667a20
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191988"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Пример
 В следующем примере проверяется на равенство с помощью экземпляров типов, которые ранее были определены в этой статье для демонстрации по умолчанию и правильное поведение для оператора равенства.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 В этом примере формируются следующие данные:

 **Неверный тип: {2,2} {2,2} равны? Не**
**удобно: {3,3} {3,3} равны? Да**
**удобно: {3,3} {3,3} являются ==?   Да**
**неверный тип: {2,2} {9,9} равны? Не**
**удобно: {3,3} {9,9} являются ==?   Нет**
## <a name="see-also"></a>См. также
 [Операторы равенства](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



