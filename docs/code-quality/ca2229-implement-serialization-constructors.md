---
title: CA2229. Реализуйте конструкторы сериализации
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d148efb87c8516b34342a8c9d16b63364a2eae16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231010"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229. Реализуйте конструкторы сериализации

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не является делегатом или интерфейсом, и одно из следующих условий имеет значение true:

- Тип не имеет конструктора, принимающего <xref:System.Runtime.Serialization.SerializationInfo> объект <xref:System.Runtime.Serialization.StreamingContext> и объект (сигнатура конструктора сериализации).

- Тип является незапечатанным, а модификатор доступа для его конструктора сериализации не защищен (Family).

- Тип запечатан, а модификатор доступа для его конструктора сериализации не является закрытым.

## <a name="rule-description"></a>Описание правила

Это правило относится к типам, поддерживающим пользовательскую сериализацию. Тип поддерживает пользовательскую сериализацию, если он реализует <xref:System.Runtime.Serialization.ISerializable> интерфейс. Конструктор сериализации необходим для десериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации. Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не следует подавлять нарушение правила. Тип не будет десериализуемым и не будет работать во многих сценариях.

## <a name="example"></a>Пример

В следующем примере показан тип, удовлетворяющий правилу.

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Связанные правила

[CA2237. Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
