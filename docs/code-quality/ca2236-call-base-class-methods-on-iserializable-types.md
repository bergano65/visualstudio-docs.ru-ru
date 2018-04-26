---
title: 'CA2236: вызывайте методы базового класса для типов ISerializable'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81ea72439219431ee0a1a5403aa266e1b2601a78
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: вызывайте методы базового класса для типов ISerializable
|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип является производным от типа, который реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и одно из следующих условий верно:

-   Тип реализует конструктор сериализации, то есть конструктор с <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> сигнатура параметра, но не вызывает конструктор сериализации базового типа.

-   Тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метода, но не вызывает <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод базового типа.

## <a name="rule-description"></a>Описание правила
 В процессе настраиваемой сериализации, реализуемый типом <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод сериализации его полей и выполнить десериализацию поля конструктор сериализации. Если тип является производным от типа, который реализует <xref:System.Runtime.Serialization.ISerializable> базовый тип интерфейса <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> конструктор сериализации и метод должен вызываться для сериализации или десериализации-serialize поля базового типа. В противном случае тип не быть сериализованы и десериализованный правильно. Обратите внимание, что если производный тип не добавляются все новые поля, тип нужно реализовать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод или конструктор сериализации или вызвать эквиваленты базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, вызовите базовый тип <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> производный метод или конструктор сериализации из соответствующего метода типа или конструктора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано производный тип, соответствующий правилу, вызвав конструктор сериализации и <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод базового класса.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)