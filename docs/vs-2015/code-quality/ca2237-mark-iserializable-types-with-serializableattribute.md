---
title: 'CA2237: Пометьте типы ISerializable с SerializableAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8778b0bfa035c782cf35d205fc59d463112196c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545162"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, видимый извне, реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, а тип не помечен <xref:System.SerializableAttribute?displayProperty=fullName> атрибутом. Правило игнорирует производные типы, базовый тип которых не является сериализуемым.

## <a name="rule-description"></a>Описание правила
 Чтобы общеязыковая среда выполнения была распознана как сериализуемый, типы должны быть помечены <xref:System.SerializableAttribute> атрибутом, даже если тип использует пользовательскую подпрограммы сериализации посредством реализации <xref:System.Runtime.Serialization.ISerializable> интерфейса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените <xref:System.SerializableAttribute> атрибут к типу.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила для классов исключений, так как они должны быть сериализуемыми для правильной работы в разных доменах приложений.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. Раскомментируйте <xref:System.SerializableAttribute> строку атрибута для удовлетворения правила.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236. Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240. Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229. Реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238. Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239. Обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120. Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
