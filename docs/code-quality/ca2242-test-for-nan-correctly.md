---
title: "CA2242: Выполняйте проверку NaN правильно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b79c2d180bab62239dcace4bcf5b49195d339946
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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