---
title: CA2239. Обеспечьте наличие методов десериализации в необязательных полях
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5599f111d6580f654436fdd2ff85f69f1329920d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541640"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239. Обеспечьте наличие методов десериализации в необязательных полях

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип имеет поле, которое помечено <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> атрибута и типа не предоставляет методы обработки событий десериализации.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> Атрибут не влияет на сериализацию; в поле, помеченное атрибутом сериализуется. Тем не менее поле обрабатывается при десериализации и сохраняет значение по умолчанию, связанные с его типом. Требуется задать для поля во время десериализации следует объявлять обработчики событий десериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте методы в тип обработки событий десериализации.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если поле должно игнорироваться во время процесса десериализации.

## <a name="example"></a>Пример
 В примере показан тип с необязательным полем и событий десериализации методов обработки.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)