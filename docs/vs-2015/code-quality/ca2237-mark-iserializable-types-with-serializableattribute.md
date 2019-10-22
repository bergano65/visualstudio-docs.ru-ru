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
ms.openlocfilehash: c548eb76ba36099d0cef5b651a095f35d64e033c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666697"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: пометьте типы ISerializable атрибутом SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, видимый извне, реализует интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, а тип не помечен атрибутом <xref:System.SerializableAttribute?displayProperty=fullName>. Правило игнорирует производные типы, базовый тип которых не является сериализуемым.

## <a name="rule-description"></a>Описание правила
 Для распознавания общеязыковой средой выполнения в качестве сериализуемых типы должны быть помечены атрибутом <xref:System.SerializableAttribute>, даже если тип использует настраиваемую подпрограммы сериализации посредством реализации интерфейса <xref:System.Runtime.Serialization.ISerializable>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените к типу атрибут <xref:System.SerializableAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила для классов исключений, так как они должны быть сериализуемыми для правильной работы в разных доменах приложений.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило. Раскомментируйте строку атрибута <xref:System.SerializableAttribute>, чтобы удовлетворить правилу.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
