---
title: CA1720. Идентификаторы не должны содержать имен типов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 504c985bd276a891b76e8c9b2a7c0ef51c3a490a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991965"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720. Идентификаторы не должны содержать имена типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Иногда использование имен параметров и элементов, основанные на типах может быть целесообразным. Тем не менее, для новых разработок, нет известной сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Для библиотек, ранее поставлявшихся возможно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Имена параметров не должны совпадать с именами элементов](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
