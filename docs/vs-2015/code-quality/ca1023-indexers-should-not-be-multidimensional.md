---
title: 'CA1023: Индексаторы не должны быть многомерными | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1b7c4c82add8644a1c2c213536c2ad3c0097c3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661980"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: индексы не должны быть многомерными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий более одного индекса.

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, должны использовать один индекс. Многомерные Индексаторы могут значительно снизить удобство использования библиотеки. Если для проектирования требуется несколько индексов, проверьте, представляет ли тип логическое хранилище данных. В противном случае используйте метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените структуру, чтобы она использовала одиночное целое число или индекс строки, или используйте вместо индексатора метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила только после тщательного рассмотрения необходимости в нестандартном индексаторе.

## <a name="example"></a>Пример
 В следующем примере показан тип `DayOfWeek03` с многомерным индексатором, нарушающим правило. Индексатор может рассматриваться как тип преобразования и, таким образом, более соответствующим образом представлен как метод. Тип перерабатывается в `RedesignedDayOfWeek03` для удовлетворения правила.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1043: используйте целый или строковый аргумент для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)
