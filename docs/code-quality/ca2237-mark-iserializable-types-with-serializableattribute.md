---
title: CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237931"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Тип, видимый извне, реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, а тип не помечен <xref:System.SerializableAttribute?displayProperty=fullName> атрибутом. Правило игнорирует производные типы, базовый тип которых не является сериализуемым.

## <a name="rule-description"></a>Описание правила
Чтобы общеязыковая среда выполнения была распознана как сериализуемый, типы должны быть помечены <xref:System.SerializableAttribute> атрибутом, даже если тип использует пользовательскую подпрограммы сериализации посредством реализации <xref:System.Runtime.Serialization.ISerializable> интерфейса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, примените <xref:System.SerializableAttribute> атрибут к типу.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте предупреждение из этого правила для классов исключений, так как они должны быть сериализуемыми для правильной работы в разных доменах приложений.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило. Раскомментируйте <xref:System.SerializableAttribute> строку атрибута для удовлетворения правила.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2236: Вызов методов базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Правильно реализуйте интерфейс ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: Предоставление методов десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Безопасные конструкторы сериализации](../code-quality/ca2120-secure-serialization-constructors.md)