---
title: CA2235. Пометьте все несериализуемые поля
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 40a4326924d83d4604f512f41f85e7adb8d21bb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975053"
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
 Сериализуемый тип — это приложения, имеющего <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. При сериализации типа <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> возникает исключение, если тип содержит поле экземпляра типа, который не может быть сериализован.

 Исключение — если тип использует пользовательскую сериализацию с помощью <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс. Типов, реализующих этот интерфейс предоставить собственную логику сериализации, и поэтому CA2235 не сработает для поля несериализуемого экземпляров таких типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибут с полем, которое не может быть сериализован.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Только подавить предупреждение из этого правила, если <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> объявлен тип, который обеспечивает связь экземпляров с поля, чтобы сериализовать и десериализовать.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило и тип, соответствующий этому правилу.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
