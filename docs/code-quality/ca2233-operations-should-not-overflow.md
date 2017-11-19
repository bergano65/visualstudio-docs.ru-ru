---
title: "CA2233: Операции не должно быть переполнений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d8b602d83eee4be49f63eef0ee8d2cd3d77f5040
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: в операциях не должно быть переполнений
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод выполняет арифметическую операцию и не проверяет заранее операнды для предотвращения переполнения.  
  
## <a name="rule-description"></a>Описание правила  
 Не следует выполнять арифметические операции без предварительной проверки операндов, чтобы убедиться в том, что результат операции не находится за пределами диапазона возможных значений для используемых типов данных. В зависимости от контекста выполнения и используемых типов данных, арифметическое переполнение может привести к либо <xref:System.OverflowException?displayProperty=fullName> или старшие биты результата отбрасываются.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, проверьте операнды, прежде чем выполнить операцию.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если возможные значения операндов никогда не приведет к переполнению арифметической операции.  
  
## <a name="example-of-a-violation"></a>Пример нарушения  
  
### <a name="description"></a>Описание  
 В следующем примере метод управляет целым числом, нарушающий это правило. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]требуется **удалить** целое число со знаком переполнения возможность отключена для этой срабатывание.  
  
### <a name="code"></a>Код  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>Комментарии  
 Если передается в данном примере метод <xref:System.Int32.MinValue?displayProperty=fullName>, операция будет потеря точности. В этом случае наиболее значимого бита результата отбрасываются. В следующем коде показано, как это происходит.  
  
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
  
## <a name="fix-with-input-parameter-validation"></a>Исправить путем проверки входного параметра  
  
### <a name="description"></a>Описание  
 В следующем примере предыдущее нарушение устраняется путем проверки входного значения.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>Исправить с помощью проверенного блока  
  
### <a name="description"></a>Описание  
 В следующем примере предыдущее нарушение устраняется путем заключения операции в проверенный блок. Если операция вызывает переполнение, <xref:System.OverflowException?displayProperty=fullName> будет создано.  
  
 Обратите внимание, что проверенные блоки не поддерживаются в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Включение проверенного арифметического переполнения и потери точности  
 При включении проверенного арифметического переполнения или потери точности в C# это эквивалентно упаковки каждой операции целое число со знаком в проверенный блок.  
  
 **Чтобы включить проверенное арифметические переполнения и потери точности в C#**  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите **свойства**.  
  
2.  Выберите **построения** и нажмите кнопку **Дополнительно**.  
  
3.  Выберите **Проверять арифметические переполнения и потери точности** и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Операторы в C#](/dotnet/csharp/language-reference/operators/index)   
 [Операторы checked и unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)