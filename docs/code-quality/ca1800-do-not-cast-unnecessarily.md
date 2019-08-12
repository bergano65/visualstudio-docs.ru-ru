---
title: CA1800. Не делайте лишних приведений
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 942a9911d0dadbf5f130344735ca9aa504cb71fd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921595"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800. Не делайте лишних приведений

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Метод выполняет дублирование приведений к одному из своих аргументов или локальных переменных.

Для полного анализа по этому правилу тестируемая сборка должна быть построена с помощью отладочной информации, а соответствующий файл базы данных программы (PDB) должен быть доступен.

## <a name="rule-description"></a>Описание правила
Повторяющиеся приведения снижают производительность, особенно если приведения выполняются в компактных операторах итераций. При явном дублировании операций приведения результата приведения в локальную переменную и использования локальной переменной вместо повторяющихся операций приведения.

Если оператор используется для проверки того, будет ли приведение выполнено до фактического приведения, рассмотрите возможность проверки результата `as` оператора. `is` C# Это обеспечивает те же функции без неявной операции приведения, выполняемой `is` оператором. Кроме того, C# в 7,0 и более поздних `is` версиях используйте оператор с [сопоставлением шаблонов](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) для проверки преобразования типа и приведения выражения к переменной этого типа за один шаг.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените реализацию метода, чтобы максимально сокращать количество операций приведения.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила или полностью проигнорировать правило, если производительность не является проблемой.

## <a name="examples"></a>Примеры
В следующем примере показан метод, который нарушает правило с помощью C# `is` оператора. Второй метод удовлетворяет правилу, заменяя `is` оператор тестом на результат `as` оператора, что сокращает количество операций приведения на итерацию с двух до одной. Третий метод также удовлетворяет правилу, используя `is` with с сопоставлением [шаблонов](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) для создания переменной требуемого типа, если преобразование типа будет выполнено.

[!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

В следующем примере показан метод, `start_Click`который содержит несколько повторяющихся явных приведений, которые нарушают правило, и метод, `reset_Click`который удовлетворяет правилу путем сохранения приведения в локальной переменной.

[!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
[!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>См. также

- [как (C# ссылка)](/dotnet/csharp/language-reference/keywords/as)
- [имеет (C# ссылка)](/dotnet/csharp/language-reference/keywords/is)