---
title: 'CA1043: используйте целый или строковый аргумент для индексаторов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad1a25f33ce91fba7b2be8723b86067afe81632c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: используйте целый или строковый аргумент для индексаторов
|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатора, который использует тип индекса, отличное от <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, или <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, следует использовать типы целочисленного или строкового индекса. Эти типы обычно используются для индексации структур данных и повышения удобства использования библиотеки. Использование <xref:System.Object> тип должен быть только в том случае, если во время разработки невозможно указать конкретный тип integer или string. Если для разработки требуются другие типы индекса, пересмотрите ли тип логическое хранилище данных. Если он не представляет логическое хранилище данных, используйте метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, изменить индекс для целочисленный или строковый тип или метод вместо индексатора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.

## <a name="example"></a>Пример
 В следующем примере показано индексатор, который использует <xref:System.Int32> индекса.

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1023: индексы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)