---
title: CA1043. Используйте целый или строковый аргумент для индексаторов
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f3bd308e35e36c18cf9231f7fd2ed9d9f442a9ca
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922476"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043. Используйте целый или строковый аргумент для индексаторов

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытый или защищенный индексатор, который использует тип индекса, отличное от <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, или <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Индексаторы, то есть индексированные свойства, следует использовать типы integer или string для индекса. Эти типы обычно используются для индексации структур данных и повышения удобства использования библиотеки. Использование <xref:System.Object> тип следует только в том случае, где конкретный тип integer или string не может быть указан во время разработки. Если для разработки требуются другие типы индекса, пересмотрите ли тип логическое хранилище данных. Если он не представляет логическое хранилище данных, используйте метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить индекс с типом integer или string или использовать метод вместо индексатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила только после тщательной проверки необходимости использовать нестандартный индексатор.

## <a name="example"></a>Пример
 В следующем примере показано индексатор, который использует <xref:System.Int32> индекса.

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1023: ИНДЕКСЫ Индексаторы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)