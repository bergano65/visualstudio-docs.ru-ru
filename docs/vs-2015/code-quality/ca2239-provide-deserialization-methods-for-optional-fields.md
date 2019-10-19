---
title: 'CA2239: предоставление методов десериализации для необязательных полей | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5604b697af1716e918f3a0f6d9a26ddbe70fc0b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672959"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: предоставляйте методы десериализации для необязательных полей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип имеет поле, помеченное атрибутом <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>, а тип не предоставляет методы обработки событий отмены сериализации.

## <a name="rule-description"></a>Описание правила
 Атрибут <xref:System.Runtime.Serialization.OptionalFieldAttribute> не влияет на сериализацию. поле, помеченное атрибутом, сериализуется. Однако поле не учитывается при десериализации и сохраняется со значением по умолчанию, связанным с его типом. Необходимо объявить обработчики событий десериализации, чтобы задать поле в процессе десериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте методы обработки событий отмены сериализации в тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если в процессе десериализации поле будет игнорироваться.

## <a name="example"></a>Пример
 В следующем примере показан тип с необязательным полем и методами обработки событий отмены сериализации.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
