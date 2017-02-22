---
title: "CA2233: в операциях не должно быть переполнений | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2233: в операциях не должно быть переполнений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод выполняет арифметическую операцию и предварительно не проверяет операнды для предотвращения переполнения.  
  
## Описание правила  
 Для выполнения арифметических операций сначала должны быть проверены операнды, чтобы удостовериться в том, что результат операции находится в диапазоне возможных значений для используемых типов данных.  В зависимости от контекста выполнения и используемых типов данных, арифметическое переполнение может приводить к <xref:System.OverflowException?displayProperty=fullName> или пропуску старших разрядов результата.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, перед выполнением операции проверьте операнды.  
  
## Отключение предупреждений  
 Предупреждение из этого правила можно отключить без последствий, если арифметические значения операндов никогда не приведут к переполнению арифметической операции.  
  
## Пример нарушения  
  
### Описание  
 В следующем примере метод управляет целым числом, нарушающим это правило.  Для срабатывания [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] требуется, чтобы параметр переполнения целого числа **Remove** был отключен.  
  
### Код  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Комментарии  
 Если бы метод в этом примере был передан <xref:System.Int32.MinValue?displayProperty=fullName>, то произошло бы переполнение операции.  В этом случае старшие разряды результата отбрасываются.  В следующем коде показано, как это происходит.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Output  
  
```  
2147483647  
```  
  
## Исправление путем проверки входного параметра  
  
### Описание  
 В следующем примере осуществляется исправление ранее возникшего нарушения путем проверки входного значения.  
  
### Код  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## Исправление с помощью проверенного блока  
  
### Описание  
 В следующем примере осуществляется исправление ранее возникшего нарушения путем заключения операции в проверенный блок.  Если операция вызывает переполнение, возникает <xref:System.OverflowException?displayProperty=fullName>.  
  
 Следует помнить, что проверенные блоки не поддерживаются в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### Код  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## Включение проверенного арифметического переполнения\/потери точности  
 Включение проверенного арифметического переполнения\/потери точности в C\# эквивалентно заключению каждой операции с целым числом в проверенный блок.  
  
 **Чтобы включить проверенное арифметическое переполнение\/потерю точности в C\#**  
  
1.  В **Обозревателе решений** щелкните правой кнопкой мыши проект и выберите команду **Свойства**.  
  
2.  Перейдите на вкладку **Построение** и щелкните **Дополнительно**.  
  
3.  Измените свойство **Проверять арифметические переполнения и потери точности** и нажмите **ОК**.  
  
## См. также  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Операторы C\#](/dotnet/csharp/language-reference/operators/index)   
 [Checked и Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)