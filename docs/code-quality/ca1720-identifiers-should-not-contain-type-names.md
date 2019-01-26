---
title: CA1720. Идентификаторы не должны содержать имена типов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d56b2d3ae58a3cb24042c4bd4befdd2b92bae3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037217"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720. Идентификаторы не должны содержать имена типов

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя параметра в доступном члене содержит имя типа данных.

 - или -

 Имя видимого элемента содержит имя типа данных для конкретного языка.

## <a name="rule-description"></a>Описание правила
 Имена параметров и элементов лучше используются для обмена данными их значение не описывали их тип, который должен предоставляться средствами разработки. Для имен членов Если необходимо использовать имя типа данных, используйте независимые от языка имя вместо конкретного языка. Например вместо C# имени типа «int», используйте имя типа данных независимый от языка, Int32.

 Каждый маркер дискретных имя параметра или члена проверяется следующие имена типов данных конкретного языка, без учета регистра:

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Int

- Целое число без знака

- Целое число

- UInteger

- Long

- ULong

- Без знака

- Со знаком

- Float

- float32

- float64

Кроме того, имена параметра также проверяются следующие имена типов данных вне зависимости от языка, без учета регистра:

- Object

- OBJ

- Boolean

- Char

- String

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- PTR

- Указатель

- UInptr

- UPtr

- UPointer

- Single

- Double

- Десятичное число

- Guid

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **Нарушение параметра.**

 Замените идентификатор типа данных, имени параметра условие, которое лучше описывает назначение или более универсальный термин, такой как «value».

 **Нарушение члена.**

 Замените идентификатор типа данных языковое имя члена условие, которое лучше описывает его значения, эквивалентные независимый от языка или более универсальный термин, такой как «value».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Иногда использование имен параметров и элементов, основанные на типах может быть целесообразным. Тем не менее, для новых разработок, нет известной сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Для библиотек, которые были предоставлены ранее возможно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Имена параметров не должны совпадать с именами элементов](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
