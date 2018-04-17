---
title: 'CA1814: Используйте ступенчатые массивы вместо многомерных | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f87c0141b437cebce2531b5b1ec4cd983fa1822
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: используйте ступенчатые массивы вместо многомерных
|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Член объявлен как многомерный массив.  
  
## <a name="rule-description"></a>Описание правила  
 Массив массивов — это массив, элементы которого сами являются массивами. Массивы, которые составляют элементы, могут иметь различные размеры, что позволяет экономить пространство для некоторых наборов данных.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, преобразуйте многомерный массив в массив массивов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, если многомерный массив не расходует место.  
  
## <a name="example"></a>Пример  
 В следующем примере показано объявления для массивов и многомерных массивов.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]