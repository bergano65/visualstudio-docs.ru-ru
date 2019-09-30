---
title: CA1502. Избегайте чрезмерной сложности
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f26faf16cc8a9a8235596aef68e5af5c3b4401e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253305"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502. Избегайте чрезмерной сложности

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Метод имеет чрезмерную сложностью организации циклов сложность.

## <a name="rule-description"></a>Описание правила

*Сложность сложностью организации циклов* измеряет количество линейно независимых путей с помощью метода, который определяется числом и сложностью условных ветвей. Низкая сложностью организации циклов сложность обычно указывает на метод, который прост в понимании, тестировании и обслуживании. Сложность сложностью организации циклов вычисляется на основе графа потока управления метода и предоставляется следующим образом:

сложностью организации циклов сложность = количество граней — количество узлов + 1.

*Узел* представляет логическую точку ветвления, а *ребро* — линию между узлами.

Правило сообщает о нарушении, если сложность сложностью организации циклов превышает 25.

Дополнительные сведения о метриках кода можно узнать по [мере сложности управляемого кода](../code-quality/code-metrics-values.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, выполните рефакторинг метода, чтобы уменьшить его сложностью организации циклов сложность.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Вы можете отключить предупреждение из этого правила, если сложность не может быть легко сокращена и метод прост в понимании, тестировании и обслуживании. В частности, метод, содержащий крупный `switch` оператор (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), является кандидатом для исключения. Риск дестабилизации базы кода в конце цикла разработки или внесения непредвиденных изменений в поведение во время выполнения в ранее отгруженном коде может привести к перегрузке преимуществ поддержки при рефакторинге кода.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Как вычисляется сложность сложностью организации циклов

Сложность сложностью организации циклов вычисляется путем добавления 1 к следующему:

- Количество ветвей (например `if`, `while`, и `do`)

- `case` Количество инструкций в`switch`

## <a name="example"></a>Пример

В следующих примерах показаны методы с различной сложностью организации циклов сложностью.

**Сложностью организации циклов сложность 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Пример

**Сложностью организации циклов сложность 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Пример

**Сложностью организации циклов сложность 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Пример

**Сложностью организации циклов сложность 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Связанные правила

[CA1501 Избегайте чрезмерного наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>См. также

- [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)