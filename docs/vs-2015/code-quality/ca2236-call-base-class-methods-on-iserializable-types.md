---
title: CA2236. Вызывайте методы базового класса для типов ISerializable | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4ec8c14da5c691f6f9740c6df86cb38aeb9fac5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142391"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236. Вызывайте методы базового класса для типов ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: СЛЕДУЕТ Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
