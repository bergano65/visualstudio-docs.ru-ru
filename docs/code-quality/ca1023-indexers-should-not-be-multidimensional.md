---
title: "CA1023: Индексы не должны быть многомерными | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3b677f4cde4a38b2e682e36090e7a86f68e4fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: индексы не должны быть многомерными
|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип содержит открытый или защищенный индексатор, который использует более одного индекса.  
  
## <a name="rule-description"></a>Описание правила  
 Индексаторы, то есть индексированные свойства, должны использовать один индекс. Многомерные индексаторы могут крайне отрицательно сказаться удобства использования библиотеки. Если для разработки требуются несколько индексов, пересмотрите ли тип логическое хранилище данных. В противном случае используйте метод.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, изменить проект, чтобы использовать единственный целочисленный или строковый индекс, или используйте вместо индексатора метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `DayOfWeek03`, с многомерным индексатором, который нарушает правила. Индексатор можно рассматривать как тип преобразования и поэтому более качественной предоставляется как метод. Тип модернизирован в `RedesignedDayOfWeek03` в соответствии с правилом.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1043: используйте целый или строковый аргумент для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)