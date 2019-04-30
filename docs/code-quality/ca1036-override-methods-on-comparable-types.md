---
title: CA1036. Переопределите методы в сопоставимых типах
ms.date: 03/11/2019
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
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779000"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036. Переопределите методы в сопоставимых типах

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип реализует <xref:System.IComparable?displayProperty=fullName> интерфейс и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает языковой оператор равенства, неравенства, менее- или больше — чем. Правило сообщает о нарушениях, если тип наследует только реализацию интерфейса.

По умолчанию это правило считывает только открытые и защищенные типы, но это [можно настроить](#configurability).

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

Его можно безопасно подавить предупреждение из правила CA1036 при нарушение причиной является отсутствие операторов и язык программирования не поддерживает перегрузку операторов, как в случае с Visual Basic. Если выяснилось, что реализация операторов не имеет смысла в контексте приложения, его можно безопасно подавить предупреждение из этого правила, при его срабатывании на равенство операторов, отличных от функции op_Equality. Тем не менее, всегда следует переопределить функции op_Equality и оператора ==, если переопределить <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="examples"></a>Примеры

Следующий код содержит тип, который правильно реализует <xref:System.IComparable>. Комментарии к коду определить методы, которые удовлетворяют различные правила, которые связаны с <xref:System.Object.Equals%2A> и <xref:System.IComparable> интерфейс.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Следующий код приложения проверяет поведение <xref:System.IComparable> реализацию, которая была показана ранее.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)