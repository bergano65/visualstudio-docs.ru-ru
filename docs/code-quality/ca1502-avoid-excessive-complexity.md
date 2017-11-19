---
title: "CA1502: Избегайте чрезмерной сложности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c45ca232b555af1441502586a38c80f43c41edc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: избегайте чрезмерной сложности
|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод имеет чрезмерного цикломатическую сложность.  
  
## <a name="rule-description"></a>Описание правила  
 *Сложность* измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей. Низкий цикломатическую сложность обычно указывает метод, который можно легко понять, проверки и поддержки. Цикломатическую сложность вычисляется на основе диаграммы потока управления метода и задается следующим образом:  
  
 сложность = количество граней - количество узлов + 1  
  
 где узел представляет логическую точку ветвления и граница представляет линию между узлами.  
  
 Правило приводит к нарушению, если более 25 цикломатическую сложность.  
  
 Дополнительные сведения о метриках кода в [Оценка сложности и удобства поддержки управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, выполните рефакторинг метода, чтобы снизить цикломатическую сложность.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если трудно уменьшить сложность и метод легко понять, проверки и поддержки. В частности, метод, который содержит большой `switch` (`Select` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) инструкция является кандидатом для исключения. Риск дестабилизации базового позднее в процессе цикла разработки или внесения непредвиденных изменений в поведение времени выполнения ранее поставленного кода может перевесить преимущества удобства поддержки оптимизации кода кода.  
  
## <a name="how-cyclomatic-complexity-is-calculated"></a>Вычисление цикломатическую сложность  
 Цикломатическую сложность рассчитывается путем сложения 1 следующее:  
  
-   Количество ветвей (например, `if`, `while`, и `do`)  
  
-   Количество `case` инструкций в`switch`  
  
 В следующих примерах показано методы, которые имеют различные цикломатическую сложность.  
  
## <a name="example"></a>Пример  
 **Цикломатическую сложность 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## <a name="example"></a>Пример  
 **Цикломатическую сложность 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## <a name="example"></a>Пример  
 **Цикломатическую сложность 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## <a name="example"></a>Пример  
 **Сложность 8.**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1501: избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## <a name="see-also"></a>См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)