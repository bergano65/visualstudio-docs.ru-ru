---
title: 'CA2242: правильно выполняйте проверку NaN'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c87b3e3528f12c07f728a5b82b56e75ee6551c1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: правильно выполняйте проверку NaN
|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выражение проверяет значение на <xref:System.Single.NaN?displayProperty=fullName> или <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Double.NaN?displayProperty=fullName>, который представляет не является числовым, результаты при арифметической операции не определено. Любое выражение, которое проверяет равенство значение и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `false`. Любое выражение, которое проверяет неравенство значения и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и точно определить, представляет ли значение <xref:System.Double.NaN?displayProperty=fullName>, используйте <xref:System.Single.IsNaN%2A?displayProperty=fullName> или <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два выражения, которые неправильно протестировать значения с <xref:System.Double.NaN?displayProperty=fullName> и выражение, использующее правильно <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]