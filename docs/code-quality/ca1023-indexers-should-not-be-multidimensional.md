---
title: "CA1023: индексы не должны быть многомерными | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023: индексы не должны быть многомерными
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий несколько индексов.  
  
## Описание правила  
 Индексаторы, то есть индексированные свойства, должны использовать один индекс.  Многомерные индексаторы могут крайне отрицательно сказаться на удобстве работы с библиотекой.  Если в программе требуется использовать несколько индексом, проверьте еще раз, представляет ли тип логическое хранилище данных.  Если не представляет, используйте метод.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените структуру программы таким образом, чтобы использовать единственный целочисленный или строковый индекс, или используйте вместо индексатора метод.  
  
## Отключение предупреждений  
 Предупреждения о нарушении этого правила следует отключать только после тщательной проверки необходимости использовать нестандартный индексатор.  
  
## Пример  
 В следующем примере показан тип `DayOfWeek03` с многомерным индексатором, который нарушает данное правило.  Можно увидеть, что данный индексатор представляет собой некоторый тип преобразования, и поэтому его более правильно использовать в качестве метода.  Чтобы устранить нарушение правила, данный тип был переработан в `RedesignedDayOfWeek03`.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Связанные правила  
 [CA1043: используйте целый или строковый аргумент для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)