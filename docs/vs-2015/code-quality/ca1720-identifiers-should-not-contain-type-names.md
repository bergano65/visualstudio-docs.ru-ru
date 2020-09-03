---
title: 'CA1720: идентификаторы не должны содержать имена типов | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f6d228b0fbf5507ba135f9ddc35d6d8b161f0011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534853"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720. Идентификаторы не должны содержать имена типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя параметра во внешнем видимом члене содержит имя типа данных.

 -или-

 Имя видимого снаружи элемента содержит имя типа данных, зависящее от языка.

## <a name="rule-description"></a>Описание правила
 Имена параметров и элементов лучше использовать для сообщения о своем значении, чем для описания их типа, который должен предоставляться средствами разработки. Для имен элементов, если необходимо использовать имя типа данных, используйте не зависящее от языка имя. Например, вместо имени типа "int" в C# используйте имя типа данных Int32, не зависящее от языка.

 Каждый дискретный токен в имени параметра или члена проверяется на соответствие следующим именам типов данных, относящихся к конкретному языку, без учета регистра:

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Int

- UInt

- Целое число

- UInteger

- Long

- ULong

- Без знака

- Со знаком

- Float

- Float32

- Float64

  Кроме того, имена параметров также проверяются по следующим независимым от языка именам типов данных без учета регистра.

- Объект

- Расширением

- Логическое

- CHAR

- Строка

- SByte

- Byte

- убите

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Указатель

- Указатель

- уинптр

- уптр

- упоинтер

- Single

- Double

- Decimal

- Guid

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **При срабатывании параметра:**

 Замените идентификатор типа данных в имени параметра на термин, который лучше описывает его значение или более универсальный термин, например "value".

 **Если срабатывает для члена:**

 Замените идентификатор типа данных, зависящий от языка, в имени члена на термин, который лучше описывает его значение, независимый от языка эквивалент или более универсальный термин, например "value".

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Иногда может быть целесообразно использовать имена параметров и членов на основе типов. Однако для новой разработки не происходит никаких известных ситуаций, при которых следует подавлять предупреждение из этого правила. Для библиотек, которые были отгружены ранее, может потребоваться отключить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707. Идентификаторы не должны содержать символы подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719. Имена параметров не должны совпадать с именами членов](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
