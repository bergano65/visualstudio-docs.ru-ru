---
title: 'CA1043: используйте целочисленный или строковый аргумент для индексаторов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03d21a824d2d3a9151dad139575f32e3417cbd39
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546839"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043. Используйте целый или строковый аргумент для индексаторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатор, использующий тип индекса, отличный от <xref:System.Int32?displayProperty=fullName> , <xref:System.Int64?displayProperty=fullName> , <xref:System.Object?displayProperty=fullName> или <xref:System.String?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, должны использовать целочисленный или строковый тип для индекса. Эти типы обычно используются для индексирования структур данных и повышения удобства использования библиотеки. Использование <xref:System.Object> типа должно быть ограничено теми случаями, когда конкретный целочисленный или строковый тип не может быть указан во время разработки. Если для создания индекса требуются другие типы, проверьте, представляет ли тип логическое хранилище данных. Если он не представляет логическое хранилище данных, используйте метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените индекс на целочисленный или строковый тип или используйте вместо индексатора метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила только после тщательного рассмотрения необходимости в нестандартном индексаторе.

## <a name="example"></a>Пример
 В следующем примере показан индексатор, использующий <xref:System.Int32> индекс.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1023. Индексы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024. По возможности используйте свойства](../code-quality/ca1024-use-properties-where-appropriate.md)
