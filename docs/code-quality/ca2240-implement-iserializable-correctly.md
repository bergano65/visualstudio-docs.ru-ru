---
title: CA2240. Правильно реализуйте ISerializable
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1924b86945df73ccd84f1215367d44d9ead039aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971290"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240. Правильно реализуйте ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Видимый извне тип может быть назначен для <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и одну из следующих условий верно:

- Тип наследуется, но не переопределяет <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод и тип объявляет поля экземпляра, которые не помечены <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибута.

- Тип не является запечатанным и тип реализует <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод, который не является внешней и переопределяемым.

## <a name="rule-description"></a>Описание правила
 Поля, объявленные в тип, наследующий экземпляров <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейса не добавляются автоматически в процессе сериализации. Чтобы включить поля, тип должен реализовывать <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и конструктор сериализации. Если поля не должны быть сериализованы, примените <xref:System.NonSerializedAttribute> атрибут для поля, чтобы явно указать решение.

 В типах, которые не являются запечатанными, реализации <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод должен быть видимый извне. Таким образом метод может вызываться с помощью производных типов и переопределяемым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> метод и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены с <xref:System.NonSerializedAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано два сериализуемые типы, которые нарушают данное правило.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Пример
 В следующем примере устраняется двух предыдущих нарушений, предоставляя можно переопределить реализацию <xref:System.Runtime.Serialization.ISerializable.GetObjectData> на класс Book, а также предоставляя реализацию `GetObjectData` библиотеки класса.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)