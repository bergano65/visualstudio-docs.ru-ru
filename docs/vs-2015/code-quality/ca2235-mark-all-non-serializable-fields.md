---
title: 'CA2235: Пометьте все несериализуемые поля | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fab79fd4daab98c6cade9271b32c45b5ae4b4332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545201"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235. Пометьте все несериализуемые поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.

## <a name="rule-description"></a>Описание правила
 Сериализуемый тип — это один из них, помеченный <xref:System.SerializableAttribute?displayProperty=fullName> атрибутом. При сериализации типа <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> создается исключение, если тип содержит поле экземпляра типа, который не является сериализуемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибут к полю, которое не является сериализуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключать предупреждение из этого правила следует только в том случае <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> , если объявлен тип, позволяющий сериализовать и десериализовать экземпляры поля.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило, и тип, соответствующий правилу.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236. Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240. Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229. Реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238. Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239. Обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120. Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
