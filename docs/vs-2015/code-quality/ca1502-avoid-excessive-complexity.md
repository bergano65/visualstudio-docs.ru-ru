---
title: 'CA1502: Избегайте чрезмерной сложности | Документация Майкрософт'
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
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0f81efa03c3955114561e923c232e8ee81dd2af6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259081"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: избегайте чрезмерной сложности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод имеет чрезмерной цикломатической сложностью.

## <a name="rule-description"></a>Описание правила
 *Сложность организации циклов* измеряет число линейно независимых путей в методе, который определяется числом и сложностью условных ветвей. Как правило, низкая сложность указывает метод, который проще воспринимать, тестировать и поддерживать. Сложность организации циклов вычисляется на основе диаграммы потока управления метода и задается следующим образом:

 сложность организации циклов = количеству краев - количество узлов + 1

 где узел представляет логическую точку ветвления и ребро представляет линию между узлами.

 Правило сообщает о нарушение при более чем 25 цикломатической сложности.

 Дополнительные сведения о метриках кода в [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполнить рефакторинг метода, чтобы снизить его сложность организации циклов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если трудно уменьшить сложность и проще воспринимать, тестировать и поддерживать метод. В частности, метод, который содержит большой `switch` (`Select` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) инструкция является кандидатом для исключения. Риском нарушения стабильности кодовая база, позднее в цикле разработки или внесения непредвиденных изменений в поведение во время выполнения в ранее выпущенном коде может перевесить преимущества удобства поддержки оптимизации кода.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Как вычисляется сложность организации циклов
 Сложность организации циклов рассчитывается путем сложения 1 следующим:

-   Количество ветвей (таких как `if`, `while`, и `do`)

-   Число `case` инструкций в `switch`

 Ниже приведены примеры методов, имеющих различные цикломатической сложности.

## <a name="example"></a>Пример
 **Сложность организации циклов 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Пример
 **Сложность организации циклов 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Пример
 **Сложность организации циклов 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Пример
 **Сложность организации циклов 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Связанные правила
 [CA1501: избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>См. также
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



