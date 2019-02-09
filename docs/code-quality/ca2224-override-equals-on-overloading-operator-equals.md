---
title: CA2224. Переопределяйте Equals при перегрузке оператора равенства
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6bfa5b590d330d791eb8c735099e619ffaf3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922970"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224. Переопределяйте Equals при перегрузке оператора равенства

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

Оператор равенства должен быть синтаксически удобный способ доступа к функциям <xref:System.Object.Equals%2A> метод. При реализации оператора равенства, логику необходимо быть идентична <xref:System.Object.Equals%2A>.

Компилятор C# выдает предупреждение, если код нарушает это правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, следует либо удалите реализацию оператора равенства, либо переопределить <xref:System.Object.Equals%2A> и иметь два метода возвращает те же значения. Если оператор равенства не вводит непредсказуемому поведению, можно устранить нарушение, предоставляющего реализацию <xref:System.Object.Equals%2A> , который вызывает <xref:System.Object.Equals%2A> метод в базовом классе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Это безопасно подавить предупреждение из этого правила, если оператор равенства возвращает то же значение, что унаследованной реализации <xref:System.Object.Equals%2A>. Примеры в этой статье включают тип, который может безопасно подавить предупреждение из этого правила.

## <a name="examples-of-inconsistent-equality-definitions"></a>Примеры определений несогласованные равенства

В примере показан тип с несогласованные определения равенства. `BadPoint` изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A> , чтобы он ведет себя идентично.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Следующий код проверяет поведение `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

В этом примере выводятся следующие данные:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

В примере показан тип, который технически нарушает это правило, но не работает должным образом несогласованности.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Следующий код проверяет поведение `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

В этом примере выводятся следующие данные:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Пример класса

В следующем примере класса (ссылочный тип), который нарушает это правило.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

В следующем примере устраняется нарушение путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Пример структуры

В следующем примере структура (тип значения), который нарушает это правило:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

В следующем примере устраняется нарушение путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Связанные правила

[CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Оператор дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)