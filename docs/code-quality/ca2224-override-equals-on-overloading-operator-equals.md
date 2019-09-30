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
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231221"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224. Переопределяйте Equals при перегрузке оператора равенства

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

Оператор равенства должен быть синтаксически удобным способом доступа к функциональности <xref:System.Object.Equals%2A> метода. При реализации оператора равенства его логика должна быть идентична этой <xref:System.Object.Equals%2A>.

Если C# код нарушает это правило, компилятор выдает предупреждение.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, необходимо либо удалить реализацию оператора равенства, либо переопределить <xref:System.Object.Equals%2A> , чтобы два метода возвращали одинаковые значения. Если оператор равенства не приводит к несогласованному поведению, можно устранить нарушение, предоставив реализацию <xref:System.Object.Equals%2A> , которая <xref:System.Object.Equals%2A> вызывает метод в базовом классе.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно спокойно отключить предупреждение из этого правила, если оператор равенства возвращает то же значение, что и унаследованная реализация <xref:System.Object.Equals%2A>. Примеры в этой статье включают тип, который может безопасно отключить предупреждение из этого правила.

## <a name="examples-of-inconsistent-equality-definitions"></a>Примеры непротиворечивых определений равенства

В следующем примере показан тип с непротиворечивыми определениями равенства. `BadPoint`изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A> его таким образом, что он ведет себя одинаково.

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

В следующем примере показан тип, который технически нарушает данное правило, но не работает в несогласованном режиме.

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

В следующем примере показан класс (ссылочный тип), нарушающий это правило.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

В следующем примере нарушение устраняется путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Пример структуры

В следующем примере показана структура (тип значения), которая нарушает это правило:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

В следующем примере нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Связанные правила

[CA1046: Не перегружать оператор Equals в ссылочных типах](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225 Перегрузки операторов имеют именованные варианты](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Операторы должны иметь симметричные перегрузки](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Переопределять GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)