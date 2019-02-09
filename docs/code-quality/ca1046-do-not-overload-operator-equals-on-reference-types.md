---
title: CA1046. Не перегружайте оператор равенства для ссылочных типов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f9304fcd86a9b36a729b1436fe16471b449ac0d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953767"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046. Не перегружайте оператор равенства для ссылочных типов

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытом или вложенном открытый ссылочный тип перегружает оператор равенства.

## <a name="rule-description"></a>Описание правила
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов. По умолчанию две ссылки равны, если они указывают на один объект.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите реализацию оператора равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если ссылочный тип ведет себя как встроенного типа значения. Если он имеет значение для выполнения сложения или вычитания для экземпляров типа, верно, вероятно, реализует оператор равенства и подавить нарушение.

## <a name="example"></a>Пример
 Следующий пример демонстрирует поведение по умолчанию при сравнении двух ссылок.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Пример

Следующее приложение сравниваются несколько ссылок.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

В этом примере выводятся следующие данные:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Связанные правила

[CA1013: Перегружайте оператор равенства при перегрузке Добавление и вычитание](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>См. также

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)