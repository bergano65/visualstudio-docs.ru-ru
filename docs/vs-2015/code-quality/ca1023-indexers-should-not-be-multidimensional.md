---
title: CA1023. Индексаторы не должны быть многомерными | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b9cf9cd97dd50577a466ed4d433e0e1dbd5da4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158034"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023. Индексы не должны быть многомерными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий более одного индекса.

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, должны использовать один индекс. Многомерные индексаторы могут существенно снизить удобство использования библиотеки. Если в программе требуется несколько индексов, пересмотрите ли тип логическое хранилище данных. В противном случае используется метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить структуру использовать единственный целочисленный или строковый индекс или использовать метод вместо индексатора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.

## <a name="example"></a>Пример
 В следующем примере показано типом, `DayOfWeek03`, с помощью многомерных индексатора, которое нарушает правило. Индексатор можно рассматривать как тип преобразования и поэтому более качественной представляется как метод. Изменен механизм функционирования тип в `RedesignedDayOfWeek03` в соответствии с правилом.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1043: Используйте целый или строковый аргумент для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)
