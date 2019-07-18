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
ms.openlocfilehash: 7ccc7819de8e79cae86a60fd015e6b8268c2456c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541653"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и тип не помечен атрибутом <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. Правило не учитывает производных типов, базовый тип которого не может быть сериализован.

## <a name="rule-description"></a>Описание правила
 Распознаваемых среда CLR как сериализуемый, типы должны быть помечены <xref:System.SerializableAttribute> атрибута, даже если тип использует пользовательскую процедуру сериализации посредством реализации <xref:System.Runtime.Serialization.ISerializable> интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.SerializableAttribute> к типу атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила для классов исключений, так как они должны быть сериализуемыми, для правильной работы между доменами приложений.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило. Раскомментируйте <xref:System.SerializableAttribute> атрибут строки в соответствии с правилом.

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)