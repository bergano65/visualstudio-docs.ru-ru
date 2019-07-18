---
title: CA2235. Помечайте все несериализуемые поля | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 542ace3c1e73454884fb341f5f9e38cf09d86396
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201555"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235. Пометьте все несериализуемые поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.

## <a name="rule-description"></a>Описание правила
 Сериализуемый тип — это приложения, имеющего <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. При сериализации типа <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> исключение вызывается в том случае, если тип содержит поле экземпляра типа, который не может быть сериализован.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибут с полем, которое не может быть сериализован.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Только подавить предупреждение из этого правила, если <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> объявлен тип, который обеспечивает связь экземпляров с поля, чтобы сериализовать и десериализовать.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило и тип, соответствующий этому правилу.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: СЛЕДУЕТ Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
