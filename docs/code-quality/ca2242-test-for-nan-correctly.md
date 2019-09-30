---
title: CA2242. Правильно выполняйте проверку NaN
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237841"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242. Правильно выполняйте проверку NaN

|||
|-|-|
|TypeName|тестфорнанкорректли|
|CheckId|CA2242|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Выражение проверяет значение относительно <xref:System.Single.NaN?displayProperty=fullName> или. <xref:System.Double.NaN?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 <xref:System.Double.NaN?displayProperty=fullName>, представляющий нечисловое значение, если арифметическая операция не определена. Любое выражение, которое проверяет равенство между значениями <xref:System.Double.NaN?displayProperty=fullName> и всегда `false`возвращает значение. Любое выражение, которое проверяет неравенство между значениями и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `true`значение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила и точно определить, представляет <xref:System.Double.NaN?displayProperty=fullName>ли значение, используйте <xref:System.Single.IsNaN%2A?displayProperty=fullName> или <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показаны два выражения, которые неправильно проверяют значение <xref:System.Double.NaN?displayProperty=fullName> , и выражение, которое правильно <xref:System.Double.IsNaN%2A?displayProperty=fullName> использует для проверки значения.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]