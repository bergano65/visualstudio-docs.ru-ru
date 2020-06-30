---
title: 'CA2240: реализуйте интерфейс ISerializable правильно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543667"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240. Правильно реализуйте ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, видимый извне, может быть назначен <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейсу, и одно из следующих условий имеет значение true:

- Тип наследует, но не переопределяет <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод, а тип объявляет поля экземпляра, не помеченные <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибутом.

- Тип не запечатан, и тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод, который не является видимым и переопределяемым извне.

## <a name="rule-description"></a>Описание правила
 Поля экземпляров, объявленные в типе, который наследует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не включаются автоматически в процесс сериализации. Чтобы включить поля, тип должен реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и конструктор сериализации. Если поля не должны быть сериализованы, примените <xref:System.NonSerializedAttribute> атрибут к полям, чтобы явно указать решение.

 В незапечатанных типах реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метода должны быть видимыми извне. Таким образом, метод может вызываться производными типами и быть переопределяемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод видимым и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены <xref:System.NonSerializedAttribute> атрибутом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два сериализуемых типа, которые нарушают правило.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере исправляются два предыдущих нарушения, предоставляя переопределяемую реализацию [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) в классе Book и путем предоставления реализации <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> для класса Library.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2236. Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229. Реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238. Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239. Обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120. Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
