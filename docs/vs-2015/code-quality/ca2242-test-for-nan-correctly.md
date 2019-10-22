---
title: 'CA2242: неправильное тестирование NaN | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672012"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: правильно выполняйте проверку NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|тестфорнанкорректли|
|CheckId|CA2242|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выражение проверяет значение по <xref:System.Single.NaN?displayProperty=fullName> или <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Double.NaN?displayProperty=fullName>, представляющий нечисловое значение, если арифметическая операция не определена. Любое выражение, проверяющее равенство значения и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает значение `false`. Любое выражение, которое проверяет неравенство значения и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает значение `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и точно определить, представляет ли значение <xref:System.Double.NaN?displayProperty=fullName>, используйте <xref:System.Single.IsNaN%2A?displayProperty=fullName> или <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два выражения, которые неправильно проверяют значение в <xref:System.Double.NaN?displayProperty=fullName> и выражение, которое правильно использует <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
