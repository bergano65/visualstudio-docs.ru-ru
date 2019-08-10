---
title: CA1023. Индексы не должны быть многомерными
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 08a45219eb2fceeaa9c58a140990ea577c941ff7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923039"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023. Индексы не должны быть многомерными

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

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять предупреждение из этого правила только после тщательного рассмотрения необходимости в нестандартном индексаторе.

## <a name="example"></a>Пример
В следующем примере показан тип `DayOfWeek03`с многомерным индексатором, нарушающим правило. Индексатор может рассматриваться как тип преобразования и, таким образом, более соответствующим образом представлен как метод. Тип перерабатывается в `RedesignedDayOfWeek03` для удовлетворения правила.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1043 Использование целочисленного или строкового аргумента для индексаторов](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024 Используйте свойства там, где это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)