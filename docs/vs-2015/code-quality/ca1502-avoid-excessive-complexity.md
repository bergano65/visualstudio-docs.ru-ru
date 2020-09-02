---
title: 'CA1502: Избегайте чрезмерной сложности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547840"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502. Избегайте чрезмерной сложности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод имеет чрезмерную сложностью организации циклов сложность.

## <a name="rule-description"></a>Описание правила
 *Сложность сложностью организации циклов* измеряет количество линейно независимых путей с помощью метода, который определяется числом и сложностью условных ветвей. Низкая сложностью организации циклов сложность обычно указывает на метод, который прост в понимании, тестировании и обслуживании. Сложность сложностью организации циклов вычисляется на основе графа потока управления метода и предоставляется следующим образом:

 сложностью организации циклов сложность = количество граней — количество узлов + 1.

 где узел представляет логическую точку ветвления, а ребро представляет линию между узлами.

 Правило сообщает о нарушении, если сложность сложностью организации циклов превышает 25.

 Дополнительные сведения о метриках кода см. в статье [измерение сложности и удобство сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполните рефакторинг метода, чтобы уменьшить его сложностью организации циклов сложность.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Вы можете отключить предупреждение из этого правила, если сложность не может быть легко сокращена и метод прост в понимании, тестировании и обслуживании. В частности, метод, содержащий крупный `switch` `Select` оператор (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), является кандидатом для исключения. Риск дестабилизации базы кода в конце цикла разработки или внесения непредвиденных изменений в поведение среды выполнения в ранее поставленном коде может привести к перегрузке преимуществ поддержки при рефакторинге кода.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Как вычисляется сложность сложностью организации циклов
 Сложность сложностью организации циклов вычисляется путем добавления 1 к следующему:

- Количество ветвей (например,, `if` `while` и `do` )

- Количество `case` инструкций в `switch`

  В следующих примерах показаны методы с различной сложностью организации циклов сложностью.

## <a name="example"></a>Пример
 **Сложностью организации циклов сложность 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Пример
 **Сложностью организации циклов сложность 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Пример
 **Сложностью организации циклов сложность 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Пример
 **Сложностью организации циклов сложность 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Связанные правила
 [CA1501. Избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>См. также:
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
