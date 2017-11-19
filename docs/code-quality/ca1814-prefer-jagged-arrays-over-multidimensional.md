---
title: "CA1814: Используйте ступенчатые массивы вместо многомерных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa1420ab01426cbfeaaf5d70238df19fde50ea9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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