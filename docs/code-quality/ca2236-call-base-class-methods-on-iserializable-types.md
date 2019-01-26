---
title: CA2236. Вызывайте методы базового класса для типов ISerializable
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2ed7249925f066cdbba7616b368e80e7b8126bca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936012"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236. Вызывайте методы базового класса для типов ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Один тип является производным от типа, который реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и одно из следующих условий верно:

- Тип реализует конструктор сериализации, то есть конструктор с <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> сигнатура параметра, но не вызывает конструктор базового типа сериализации.

- Тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод, но не вызывает <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод базового типа.

## <a name="rule-description"></a>Описание правила
 В процессе настраиваемой сериализации, тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод сериализации его полей и конструктор сериализации для десериализации поля. Если тип является производным от типа, который реализует <xref:System.Runtime.Serialization.ISerializable> интерфейс, базовый тип <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и сериализации конструктор должен быть вызван сериализацию и десериализацию поля базового типа. В противном случае тип не быть сериализованы и десериализованный правильно. Обратите внимание, что если производный тип не добавляет никакие новые поля, тип необходимости реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод или конструктор сериализации или вызвать эквиваленты базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите базовый тип <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод или конструктор сериализации из соответствующего производного типа метода или конструктора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано производный тип, соответствующий правилу, вызвав конструктор сериализации и <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод базового класса.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)