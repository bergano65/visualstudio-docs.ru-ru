---
title: CA2235. Пометьте все несериализуемые поля
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238105"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235. Пометьте все несериализуемые поля

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.

## <a name="rule-description"></a>Описание правила

Сериализуемый тип — это один из них, помеченный <xref:System.SerializableAttribute?displayProperty=fullName> атрибутом. При сериализации типа создается <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> исключение, если тип содержит поле экземпляра типа, которое не является сериализуемым *и* не реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс.

> [!TIP]
> CA2235 не срабатывает для полей экземпляров типов, которые реализуют <xref:System.Runtime.Serialization.ISerializable> , так как они предоставляют собственную логику сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибут к полю, которое не является сериализуемым.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Отключать предупреждение из этого правила следует только <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> в том случае, если объявлен тип, позволяющий сериализовать и десериализовать экземпляры поля.

## <a name="example"></a>Пример

В следующем примере показаны два типа: один, нарушающий правило, и тот, который удовлетворяет правилу.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Примечания

Правило CA2235 не анализирует типы, реализующие <xref:System.Runtime.Serialization.ISerializable> интерфейс (если они также не помечены <xref:System.SerializableAttribute> атрибутом). Это связано с тем, что [правило CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) уже рекомендует помечать <xref:System.Runtime.Serialization.ISerializable> типы, реализующие интерфейс с <xref:System.SerializableAttribute> атрибутом.

## <a name="related-rules"></a>Связанные правила

- [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Вызов методов базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237. Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Предоставление методов десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Правильно реализуйте интерфейс ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Безопасные конструкторы сериализации](../code-quality/ca2120-secure-serialization-constructors.md)