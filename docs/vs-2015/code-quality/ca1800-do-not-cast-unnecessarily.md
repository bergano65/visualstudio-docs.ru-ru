---
title: 'CA1800: Не выполняйте лишних приведений | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 558211400425f15832b39227daa29277454e665c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591549"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: не выполняйте лишних приведений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1800: не выполняйте лишних приведений](https://docs.microsoft.com/visualstudio/code-quality/ca1800-do-not-cast-unnecessarily).

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод выполняет повторяющиеся приведения на одном из своих аргументов или локальных переменных. Для завершения анализа этим правилом протестированных сборки должны быть построены с помощью отладочную информацию и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила
 Повторяющиеся приведения снижают производительность, особенно если приведения выполняются в компактных операторах итераций. Для явного приведения повторяющихся операций сохранения результата приведения в локальной переменной и используйте локальную переменную вместо дублирования операций.

 Если C# `is` оператор используется для проверки ли приведение завершится успешно, прежде чем фактическое приведение будет выполнено, вам следует протестировать результат `as` оператор вместо этого. Это обеспечивает те же функциональные возможности без неявное приведение операции, выполняемой `is` оператор.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените реализацию метода, чтобы свести к минимуму число операций приведения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или игнорировать правило полностью, если производительность не имеет значения.

## <a name="example"></a>Пример
 В примере показан метод, который нарушает правило с помощью C# `is` оператор. Второй метод, соответствующий этому правилу, заменив `is` оператор на проверку результат `as` оператор, который уменьшает число операций приведения каждой итерации с двух до одной.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Пример
 В примере показан метод, `start_Click`, который имеет несколько явных приведений, который нарушает правило и метод, `reset_Click`, которой соблюдается правило, сохраняя приведения в локальной переменной.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>См. также
 [как](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [—](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)



