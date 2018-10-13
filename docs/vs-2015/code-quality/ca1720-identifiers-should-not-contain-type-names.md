---
title: 'CA1720: Идентификаторы не должны содержать имен типов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 8dda659a746f98bfa8038156d38316729f43016c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282507"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: идентификаторы не должны содержать имен типов
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

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   Целое число без знака

-   Целое число

-   UInteger

-   Long

-   ULong

-   Без знака

-   Со знаком

-   Float

-   float32

-   float64

 Кроме того, имена параметра также проверяются следующие имена типов данных вне зависимости от языка, без учета регистра:

-   Object

-   OBJ

-   Boolean

-   Char

-   String

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   PTR

-   Указатель

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Десятичное число

-   Guid

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **Нарушение параметра.**

 Замените идентификатор типа данных, имени параметра условие, которое лучше описывает назначение или более универсальный термин, такой как «value».

 **Нарушение члена.**

 Замените идентификатор типа данных языковое имя члена условие, которое лучше описывает его значения, эквивалентные независимый от языка или более универсальный термин, такой как «value».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Иногда использование имен параметров и элементов, основанные на типах может быть целесообразным. Тем не менее, для новых разработок, нет известной сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Для библиотек, ранее поставлявшихся возможно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: имена параметров не должны совпадать с именами элементов](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)



