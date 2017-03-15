---
title: "CA1502: избегайте чрезмерной сложности | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1502: избегайте чрезмерной сложности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод отличается чрезмерной цикломатической сложностью.  
  
## Описание правила  
 *Цикломатическая сложность* измеряет количество линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей.  Низкой цикломатической сложностью, как правило, отличаются методы, которые просты для понимания, проверки и поддержки.  Цикломатическая сложность вычисляется на основе диаграммы потока управления метода в соответствии со следующим выражением:  
  
 цикломатическая сложность \= количество граней \- количество узлов \+ 1  
  
 где узел представляет логическую точку ветвления, а грань — линию между узлами.  
  
 Предупреждение о нарушении правила выводится в том случае, если цикломатическая сложность превышает значение 25.  
  
 Дополнительные сведения о метриках кода см. в [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените структуру метода, чтобы снизить цикломатическую сложность.  
  
## Отключение предупреждений  
 Отключение предупреждений данного правила безопасно в том случае, если сложность метода трудно уменьшить, а сам метод прост для понимания, проверки и поддержки.  В частности, метод, содержащий объемный оператор `switch` \(`Select` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), является первым кандидатом на исключение из этого правила.  Риск дестабилизации базового кода позднее в процессе цикла разработки или внесения непредвиденных изменений в поведение времени выполнения ранее поставленного кода может перевесить преимущества удобства поддержки, возникающие при оптимизации кода.  
  
## Процедура вычисления цикломатической сложности  
 Цикломатическая сложность вычисляется посредством добавления единицы к следующим значениям:  
  
-   Число ветвей \(таких как операторы `if`, `while` и `do`\)  
  
-   Число операторов `case` в блоке `switch`  
  
 В следующих примерах показаны методы с различной цикломатической сложностью.  
  
## Пример  
 **Цикломатическая сложность 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Пример  
 **Цикломатическая сложность 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Пример  
 **Цикломатическая сложность 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Пример  
 **Цикломатическая сложность 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Связанные правила  
 [CA1501: избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## См. также  
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)