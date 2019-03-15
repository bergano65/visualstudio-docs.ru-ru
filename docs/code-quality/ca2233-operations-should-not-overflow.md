---
title: CA2233. В операциях не должно быть переполнений
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 013571a948c6c3fdca5da3c5c9278ca21e1f3698
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869113"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233. В операциях не должно быть переполнений

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод выполняет арифметическую операцию и не проверяет операнды заранее для предотвращения переполнения.

## <a name="rule-description"></a>Описание правила

Не выполнять арифметические операции без предварительной проверки операндов, чтобы убедиться в том, что результат операции не находится за пределами диапазона возможных значений для используемых типов данных. В зависимости от контекста выполнения и используемых типов данных, арифметическое переполнение может привести либо <xref:System.OverflowException?displayProperty=fullName> или старшие биты результата отбрасываются.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, проверьте операндов, прежде чем выполнить операцию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если возможные значения операндов никогда не приведет к переполнению арифметической операции.

## <a name="example-of-a-violation"></a>Пример нарушения

В следующем примере метод управляет целое число, которое нарушает это правило. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требуется **удалить** целочисленное переполнение возможность отключена для этой срабатывание.

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

Если этот метод в этом примере передается <xref:System.Int32.MinValue?displayProperty=fullName>, операция будет потеря точности. В этом случае наиболее значимого бита результата будут отброшены. В следующем коде показано, как это происходит.

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Результат

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Исправление с помощью проверки входных параметров

В следующем примере устраняется нарушение устраняется путем проверки входного значения.

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Исправление с помощью проверенного блока

В следующем примере устраняется нарушение устраняется путем заключения операции в проверенный блок. Если операция вызывает переполнение, <xref:System.OverflowException?displayProperty=fullName> будет создано.

Проверенные блоки не поддерживаются в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Включение проверки арифметические переполнения и потери точности

При включении checked арифметические переполнения и потери точности в C# она эквивалентна упаковки каждой операции целое число в проверенный блок.

Чтобы включить проверенное арифметические переполнения и потери точности в C#:

1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите пункт **свойства**.

2.  Перейдите на вкладку **Сборка** и нажмите кнопку **Дополнительно**.

3.  Выберите **Проверять арифметические переполнения и потери точности** и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- <xref:System.OverflowException?displayProperty=fullName>
- [Операторы в C#](/dotnet/csharp/language-reference/operators/index)
- [Операторы checked и unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)