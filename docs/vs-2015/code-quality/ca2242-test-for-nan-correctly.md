---
title: CA2242. Правильно выполняйте проверку NaN | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a98ce3d213c5d9ae85bb5132a0a44e50112037
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978979"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242. Правильно выполняйте проверку NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Выражение проверяет значение на <xref:System.Single.NaN?displayProperty=fullName> или <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Double.NaN?displayProperty=fullName>, который представляет не является числовым, результаты при арифметической операции не определено. Любое выражение, которое проверяет равенство между значениями и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `false`. Любое выражение, которое проверяет неравенство значение и <xref:System.Double.NaN?displayProperty=fullName> всегда возвращает `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и точно определить, представляет ли значение <xref:System.Double.NaN?displayProperty=fullName>, использовать <xref:System.Single.IsNaN%2A?displayProperty=fullName> или <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два выражения, которые неправильно проверяют значение с <xref:System.Double.NaN?displayProperty=fullName> и выражение, которое правильно использует <xref:System.Double.IsNaN%2A?displayProperty=fullName> для проверки значения.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
