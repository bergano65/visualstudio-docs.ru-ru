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
ms.openlocfilehash: c0cd59ec30ce45c94ac3422c4271959d74073bff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920052"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239. Обеспечьте наличие методов десериализации в необязательных полях

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Тип имеет поле, помеченное <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> атрибутом, и тип не предоставляет методы обработки событий отмены сериализации.

## <a name="rule-description"></a>Описание правила
<xref:System.Runtime.Serialization.OptionalFieldAttribute> Атрибут не влияет на сериализацию; поле, помеченное атрибутом, сериализуется. Однако поле не учитывается при десериализации и сохраняется со значением по умолчанию, связанным с его типом. Необходимо объявить обработчики событий десериализации, чтобы задать поле в процессе десериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, добавьте методы обработки событий отмены сериализации в тип.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Предупреждение из этого правила можно отключить, если в процессе десериализации поле будет игнорироваться.

## <a name="example"></a>Пример
В следующем примере показан тип с необязательным полем и методами обработки событий отмены сериализации.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA2236: Вызов методов базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Правильно реализуйте интерфейс ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237. Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Безопасные конструкторы сериализации](../code-quality/ca2120-secure-serialization-constructors.md)