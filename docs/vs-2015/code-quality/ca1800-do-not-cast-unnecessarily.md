---
title: 'CA1800: не приводите необязательное преобразование | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547801"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800. Не делайте лишних приведений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод выполняет дублирование приведений к одному из своих аргументов или локальных переменных. Для полного анализа по этому правилу тестируемая сборка должна быть построена с помощью отладочной информации, а соответствующий файл базы данных программы (PDB) должен быть доступен.

## <a name="rule-description"></a>Описание правила
 Повторяющиеся приведения снижают производительность, особенно если приведения выполняются в компактных операторах итераций. При явном дублировании операций приведения результата приведения в локальную переменную и использования локальной переменной вместо повторяющихся операций приведения.

 Если оператор C# `is` используется для проверки того, будет ли приведение выполнено до фактического приведения, рекомендуется проверить результат `as` оператора. Это обеспечивает те же функции без неявной операции приведения, выполняемой `is` оператором.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените реализацию метода, чтобы максимально сокращать количество операций приведения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила или полностью проигнорировать правило, если производительность не является проблемой.

## <a name="example"></a>Пример
 В следующем примере показан метод, который нарушает правило с помощью `is` оператора C#. Второй метод удовлетворяет правилу, заменяя `is` оператор тестом на результат `as` оператора, что сокращает количество операций приведения на итерацию с двух до одной.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показан метод, `start_Click` который содержит несколько повторяющихся явных приведений, которые нарушают правило, и метод, `reset_Click` который удовлетворяет правилу путем сохранения приведения в локальной переменной.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>См. также:
 [как](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [есть](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
