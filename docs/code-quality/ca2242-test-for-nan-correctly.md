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
ms.openlocfilehash: 8912cb6eeec8009364936a42d572f4f3d83fae5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919920"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242. Правильно выполняйте проверку NaN

|||
|-|-|
|TypeName|тестфорнанкорректли|
|CheckId|CA2242|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
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