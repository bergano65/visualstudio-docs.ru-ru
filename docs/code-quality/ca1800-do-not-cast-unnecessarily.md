---
title: 'CA1800: не выполняйте лишних приведений'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 34c03adb8ff34d3590ed93264d77536c4cdff080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915573"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: не выполняйте лишних приведений
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Метод выполняет повторяющееся приведение одного из своих аргументов или локальных переменных.

Для завершения анализа этим правилом тестируемой сборки должны быть построены с использованием отладочной информации и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила
Повторяющиеся приведения снижают производительность, особенно если приведения выполняются в компактных операторах итераций. Для явного приведения повторяющихся операций сохранения результата приведения в локальной переменной и используйте локальную переменную вместо дублирования операций.

Если в C# `is` оператор используется для проверки, что приведение завершится успешно, перед выполнением фактическое приведение Попробуйте просмотреть результат `as` оператор вместо него. Это обеспечивает те же функциональные возможности без неявное приведение операцию, выполняемую `is` оператор. Также можно использовать в C# 7.0 и более поздних версиях `is` оператор с [соответствие шаблону](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) для проверки преобразования типов и преобразовать выражение переменной этого типа за один шаг.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените реализацию метода, чтобы свести к минимуму число операций приведения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или игнорировать правило полностью, если производительность не имеет значения.

## <a name="examples"></a>Примеры
 В следующем примере показано метод, который нарушает правила с помощью C# `is` оператор. Второй метод, соответствующий этому правилу, заменив `is` оператор на проверку результат `as` оператор, который уменьшает количество операций приведения в каждой итерации с двух до одной. Третий метод также выполняет правила, используя `is` с [соответствие шаблону](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) для создания переменной нужного типа, если преобразование будет выполнено успешно.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 В следующем примере показано метод `start_Click`, с несколькими повторяющимися операциями приведения, который нарушает правила и метод, `reset_Click`, которой устранено за счет хранения приведения в локальной переменной.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>См. также
[как (Справочник по C#)](/dotnet/csharp/language-reference/keywords/as)
[— (Справочник по C#)](/dotnet/csharp/language-reference/keywords/is)