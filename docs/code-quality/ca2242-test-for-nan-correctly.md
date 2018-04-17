---
title: 'CA2242: Выполняйте проверку NaN правильно | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: a782c0b3f32c9733b47ded29852e006f8ba7c1aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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