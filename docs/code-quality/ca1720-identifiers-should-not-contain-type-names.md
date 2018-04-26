---
title: 'CA1720: идентификаторы не должны содержать имен типов'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8f86037b54b2b7ad5cce1ea683341ca6656c2b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: идентификаторы не должны содержать имен типов
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя параметра в внешнего кода элементе содержит имя типа данных.

 - или -

 Имя внешнего кода элементе содержит имя типа данных для конкретного языка.

## <a name="rule-description"></a>Описание правила
 Имена параметров и членов лучше, используемые для взаимодействия их значение не описывали их тип, который должен быть предоставляются средствами разработки. Для имен членов необходимо использовать имя типа данных, используйте независимые от языка имя, если вместо конкретного языка. Например вместо C# имени типа «int», используйте имя типа данных зависит от языка программирования, Int32.

 Каждый маркер дискретных имя параметра или члена проверяется следующие имена типов данных конкретного языка, учета регистра:

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   UInt

-   Целое число

-   UInteger

-   Long

-   ULong

-   Без знака

-   Подписанный

-   Float

-   Float32

-   Float64

 Кроме того имена параметра также проверяются следующие имена типов данных зависит от языка программирования, учета регистра:

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

 Замените идентификатор типа данных в имени параметра термин, который лучше описывает назначение или более универсальный термин, такой как «value».

 **Нарушение члена.**

 Замените идентификатор типа данных зависящие от языка имя члена термин, который лучше описывает его значения, эквивалентного зависит от языка программирования или более универсальный термин, такой как «value».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Иногда использование имена членов и параметров, основанные на типах можно применять. Однако для разработки новых приложений, не известных выполняется сценарий, где необходимо подавить предупреждение из этого правила. Для библиотек, которые имеют предыдущие поставляется может потребоваться отключить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: имена параметров не должны совпадать с именами элементов](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)