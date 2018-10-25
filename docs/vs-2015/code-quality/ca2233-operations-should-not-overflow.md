---
title: 'CA2233: Операции не должно быть переполнений | Документация Майкрософт'
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
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836662"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: в операциях не должно быть переполнений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод выполняет арифметическую операцию и не проверяет операнды заранее для предотвращения переполнения.

## <a name="rule-description"></a>Описание правила
 Не следует выполнять арифметические операции без предварительной проверки операндов, чтобы убедиться в том, что результат операции не находится за пределами диапазона возможных значений для используемых типов данных. В зависимости от контекста выполнения и используемых типов данных, арифметическое переполнение может привести либо <xref:System.OverflowException?displayProperty=fullName> или старшие биты результата отбрасываются.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, проверьте операндов, прежде чем выполнить операцию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если возможные значения операндов никогда не приведет к переполнению арифметической операции.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере метод управляет целое число, которое нарушает это правило. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] требуется **удалить** целочисленное переполнение возможность отключена для этой срабатывание.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Комментарии
 Если этот метод в этом примере передается <xref:System.Int32.MinValue?displayProperty=fullName>, операция будет потеря точности. В этом случае наиболее значимого бита результата будут отброшены. В следующем коде показано, как это происходит.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Вывод

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Исправление с помощью проверки входных параметров

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение устраняется путем проверки входного значения.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Исправление с помощью проверенного блока

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение устраняется путем заключения операции в проверенный блок. Если операция вызывает переполнение, <xref:System.OverflowException?displayProperty=fullName> будет создано.

 Обратите внимание, что проверенные блоки не поддерживаются в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Включение проверки арифметические переполнения и потери точности
 При включении checked арифметические переполнения и потери точности в C# она эквивалентна упаковки каждой операции целое число в проверенный блок.

 **Чтобы включить проверенное арифметические переполнения и потери точности в C#**

1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите пункт **свойства**.

2.  Перейдите на вкладку **Сборка** и нажмите кнопку **Дополнительно**.

3.  Выберите **Проверять арифметические переполнения и потери точности** и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также
 <xref:System.OverflowException?displayProperty=fullName> [Операторы в C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked и Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



