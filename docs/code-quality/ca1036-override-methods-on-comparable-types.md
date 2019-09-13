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
ms.openlocfilehash: 2a4e04e1afdbecdc9c333ea43a52bff3123d448a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547617"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036. Переопределите методы в сопоставимых типах

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип реализует <xref:System.IComparable?displayProperty=fullName> интерфейс и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает зависящий от языка оператор на равенство, неравенство, меньше или больше. Правило не сообщает о нарушении, если тип наследует только реализацию интерфейса.

По умолчанию это правило рассматривает только открытые и защищенные типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Типы, определяющие пользовательский порядок сортировки, реализуют <xref:System.IComparable> интерфейс. <xref:System.IComparable.CompareTo%2A> Метод возвращает целочисленное значение, указывающее правильный порядок сортировки для двух экземпляров типа. Это правило определяет типы, которые задают порядок сортировки. Установка порядка сортировки подразумевает, что обычные значения равенства, неравенства, меньше и больше не применяются. При предоставлении реализации <xref:System.IComparable>необходимо также переопределить <xref:System.Object.Equals%2A> , чтобы она возвращала <xref:System.IComparable.CompareTo%2A>значения, которые соответствуют. При переопределении <xref:System.Object.Equals%2A> и написании кода на языке, поддерживающем перегрузки операторов, следует также предоставить операторы, которые <xref:System.Object.Equals%2A>соответствуют.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, переопределите <xref:System.Object.Equals%2A>. Если ваш язык программирования поддерживает перегрузку операторов, укажите следующие операторы:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

В C#для представления этих операторов используются следующие токены:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно спокойно отключить предупреждение от CA1036 правил, если нарушение вызвано отсутствием операторов, а язык программирования не поддерживает перегрузку операторов, как в случае с Visual Basic. Если определить, что реализация операторов не имеет смысла в контексте приложения, также можно отключить вывод предупреждения из этого правила, когда оно срабатывает для операторов равенства, отличных от op_Equality. Однако при переопределении <xref:System.Object.Equals%2A?displayProperty=nameWithType>можно всегда переопределять op_Equality и оператор = =.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="examples"></a>Примеры

Следующий код содержит тип, который правильно реализует <xref:System.IComparable>. Комментарии к коду определяют методы, которые соответствуют различным правилам, связанным <xref:System.Object.Equals%2A> с <xref:System.IComparable> интерфейсом и.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Следующий код приложения проверяет поведение <xref:System.IComparable> реализации, показанной ранее.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)