---
title: CA1036. Переопределите методы в сопоставимых типах
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab36be0233ad83c5f1ec23b3511937eda07940c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953000"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036. Переопределите методы в сопоставимых типах

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.IComparable?displayProperty=fullName> интерфейс и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает языковой оператор равенства, неравенства, менее- или больше — чем. Правило сообщает о нарушениях, если тип наследует только реализацию интерфейса.

## <a name="rule-description"></a>Описание правила

Типы, определяющие пользовательский порядок сортировки реализуют <xref:System.IComparable> интерфейс. <xref:System.IComparable.CompareTo%2A> Метод возвращает целочисленное значение, указывающее правильный порядок сортировки для двух экземпляров типа. Это правило определяет типы, задающие порядок сортировки. Установка порядка сортировки означает, что порядковое значение равенства, неравенства, less- и более-чем не применяются. Если предоставить реализацию <xref:System.IComparable>, обычно необходимо также переопределить <xref:System.Object.Equals%2A> , возвращающий значения, которые соответствуют <xref:System.IComparable.CompareTo%2A>. При переопределении <xref:System.Object.Equals%2A> и при написании кода на языке, который поддерживает перегрузки операторов, также необходимо предоставить операторы, которые соответствуют <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, переопределите <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, предоставьте следующие операторы:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

В C# токены, которые используются для представления этих операторов используются следующие:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из правила CA1036 при нарушение причиной является отсутствие операторов и язык программирования не поддерживает перегрузку операторов, как в случае с Visual Basic. Это также можно отключить предупреждение из этого правила, при его срабатывании на операторы равенства, отличные от функции op_Equality, если выяснится, что реализация операторов не имеет смысла в контексте приложения. Тем не менее, следует всегда через функции op_Equality и оператора ==, если переопределяет Object.Equals.

## <a name="example"></a>Пример
 Следующий пример содержит тип, который правильно реализует <xref:System.IComparable>. Комментарии к коду определить методы, которые удовлетворяют различные правила, которые связаны с <xref:System.Object.Equals%2A> и <xref:System.IComparable> интерфейс.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Пример
 Следующее приложение проверяет поведение <xref:System.IComparable> реализацию, которая была показана ранее.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)