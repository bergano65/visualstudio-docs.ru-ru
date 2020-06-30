---
title: 'CA2233: операции не должны переполнены | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545240"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233. В операциях не должно быть переполнений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод выполняет арифметическую операцию и не проверяет операнды заранее, чтобы предотвратить переполнение.

## <a name="rule-description"></a>Описание правила
 Арифметические операции не следует выполнять без предварительной проверки операндов, чтобы убедиться, что результат операции не выходит за пределы диапазона возможных значений для используемых типов данных. В зависимости от контекста выполнения и используемых типов данных арифметическое переполнение может привести либо к, <xref:System.OverflowException?displayProperty=fullName> либо к наиболее значимым битам результата.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, перед выполнением операции проверьте операнды.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если возможные значения операндов никогда не приведут к переполнению арифметической операции.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 Метод в следующем примере управляет целым числом, нарушающим это правило. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]для срабатывания этого параметра требуется отключить параметр " **Удалить** целочисленный переполнение".

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Комментарии
 Если метод в этом примере передается <xref:System.Int32.MinValue?displayProperty=fullName> , операция будет неточной. Это приводит к отмене наиболее значительного бита результата. В следующем коде показано, как это происходит.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VB

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Выходные данные

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Исправить с помощью проверки входного параметра

### <a name="description"></a>Описание
 В следующем примере исправляется предыдущее нарушение путем проверки значения входных данных.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Исправить с помощью проверенного блока

### <a name="description"></a>Описание
 В следующем примере исправляется предыдущее нарушение путем заключения операции в проверенный блок. Если операция вызывает переполнение, <xref:System.OverflowException?displayProperty=fullName> будет выдано исключение.

 Обратите внимание, что отмеченные блоки не поддерживаются в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>Код
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Включить проверенное арифметическое переполнение/потерю точности
 Если включить проверенное арифметическое переполнение или потерю точности в C#, то оно равнозначно переносу всех целочисленных операций в проверяемый блок.

 **Включение проверенного арифметического переполнения или потери точности в C #**

1. В **Обозреватель решений**щелкните правой кнопкой мыши проект и выберите пункт **свойства**.

2. Перейдите на вкладку **Сборка** и нажмите кнопку **Дополнительно**.

3. Выберите **проверка арифметического переполнения/потери точности** и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также
 <xref:System.OverflowException?displayProperty=fullName>[Операторы C#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [установлены и сняты](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
