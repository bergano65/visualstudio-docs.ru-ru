---
title: CA2229. Реализуйте конструкторы сериализации
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518a5d4f76d1c26893ae88f45bc74586654ee15c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951980"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229. Реализуйте конструкторы сериализации

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не делегате или интерфейсе, и одно из следующих условий верно:

- Тип не имеет конструктор, принимающий <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объекта и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> объекта (сигнатура конструктора сериализации).

- Тип не запечатан и модификатор доступа для конструктора сериализации не является защищенным (семейство).

- Тип является запечатанным и модификатор доступа для конструктора сериализации не является закрытым.

## <a name="rule-description"></a>Описание правила
 Это правило относится к типы, поддерживающие пользовательской сериализации. Тип поддерживает пользовательской сериализации, если он реализует <xref:System.Runtime.Serialization.ISerializable> интерфейс. Конструктор сериализации необходим для десериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации. Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте нарушение правила. Тип не будет десериализуемым и не будет работать во многих сценариях.

## <a name="example"></a>Пример
 В примере показан тип, соответствующий этому правилу.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>