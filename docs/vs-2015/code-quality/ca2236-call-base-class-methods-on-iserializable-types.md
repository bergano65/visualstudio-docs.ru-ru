---
title: 'CA2236: вызов методов базового класса для типов ISerializable | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545188"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236. Вызывайте методы базового класса для типов ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип является производным от типа, который реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, и одно из следующих условий имеет значение true:

- Тип реализует конструктор сериализации, то есть конструктор с <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> сигнатурой параметра, но не вызывает конструктор сериализации базового типа.

- Тип реализует метод, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> но не вызывает <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод базового типа.

## <a name="rule-description"></a>Описание правила
 В пользовательском процессе сериализации тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод для сериализации своих полей и конструктор сериализации для десериализации полей. Если тип является производным от типа, реализующего <xref:System.Runtime.Serialization.ISerializable> интерфейс, метод базового типа <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> и конструктор сериализации следует вызывать для сериализации или десериализации полей базового типа. В противном случае тип не будет сериализован и десериализован правильно. Обратите внимание, что если производный тип не добавляет никаких новых полей, тип не должен реализовывать метод, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> конструктор сериализации или вызывать эквиваленты базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите метод базового типа <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> или конструктор сериализации из соответствующего метода или конструктора производного типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан производный тип, который соответствует правилу путем вызова конструктора сериализации и <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метода базового класса.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2240. Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229. Реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238. Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239. Обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120. Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
