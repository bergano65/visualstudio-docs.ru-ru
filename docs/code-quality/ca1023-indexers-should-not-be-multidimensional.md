---
title: 'CA1023: Индексы не должны быть многомерными | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6d729c6aae9f328af5268bd6e03cb56c40b1b54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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