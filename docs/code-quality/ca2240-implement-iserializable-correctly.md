---
title: 'CA2240: правильно реализуйте ISerializable'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9929937fa8655e5cbb4c86eebd4dce24fcb26966
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: правильно реализуйте ISerializable
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип может быть назначен для <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и одно из следующих условий верно:

-   Тип наследуется, но не переопределяет <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод и тип объявляет экземпляр поля, которые не отмечены ни <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибута.

-   Тип не является запечатанным и тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод, который не является внешней и переопределяемым.

## <a name="rule-description"></a>Описание правила
 Экземпляр поля, объявленные в типе, который наследует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейса не добавляются автоматически в процессе сериализации. Чтобы включить поля, тип должен реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и конструктор сериализации. Если поля не должны быть сериализованы, примените <xref:System.NonSerializedAttribute> атрибут для поля, чтобы явно указать решение.

 В типах, которые не являются запечатанными, реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод силу должны быть видимыми. Таким образом метод может вызываться с помощью производных типов и переопределяемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, сделайте <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены атрибутом <xref:System.NonSerializedAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два сериализуемые типы, которые нарушают правила.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Пример
 В следующем примере два предыдущих нарушения устраняется, предоставляя переопределить реализацию <xref:System.Runtime.Serialization.ISerializable.GetObjectData> на класс Book и обеспечив реализацию `GetObjectData` на класс библиотеки.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) [CA2229: реализация конструкторов сериализации](../code-quality/ca2229-implement-serialization-constructors.md) [CA2238: правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md) [ CA2235: Помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md) [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) [CA2239: предоставляют методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
