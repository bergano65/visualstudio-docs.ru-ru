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
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177386"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235. Пометьте все несериализуемые поля

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.

## <a name="rule-description"></a>Описание правила

Сериализуемый тип — это приложения, имеющего <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. При сериализации типа <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> возникает исключение, если тип содержит поле экземпляра типа, который не может быть сериализован *и* не реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс.

> [!TIP]
> CA2235 не срабатывает для экземпляра поля типов, реализующих <xref:System.Runtime.Serialization.ISerializable> так как они предоставляют свою собственную логику сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибут с полем, которое не может быть сериализован.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Только подавить предупреждение из этого правила, если <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> объявлен тип, который обеспечивает связь экземпляров с поля, чтобы сериализовать и десериализовать.

## <a name="example"></a>Пример

В следующем примере показано два типа: один, нарушающий правило и один, соответствующий правилу.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Примечания

Правило, CA2235 не анализирует типы, реализующие <xref:System.Runtime.Serialization.ISerializable> интерфейса (если они также отмечены <xref:System.SerializableAttribute> атрибут). Это обусловлено [правило CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) уже рекомендует пометить типы, реализующие <xref:System.Runtime.Serialization.ISerializable> взаимодействовать с <xref:System.SerializableAttribute> атрибута.

## <a name="related-rules"></a>Связанные правила

- [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)