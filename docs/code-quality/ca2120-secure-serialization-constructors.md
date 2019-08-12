---
title: CA2120. Обеспечьте безопасность конструкторов сериализации
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc7f4a82b9a75e4d189e969712472f06b4019b73
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920880"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120. Обеспечьте безопасность конструкторов сериализации

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не является делегатом или интерфейсом и объявлен в сборке, допускающей частично доверенные вызывающие объекты. Тип имеет конструктор, принимающий <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объект <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> и объект (сигнатура конструктора сериализации). Этот конструктор не защищен проверкой безопасности, но один или несколько обычных конструкторов в типе защищены.

## <a name="rule-description"></a>Описание правила
Это правило относится к типам, поддерживающим пользовательскую сериализацию. Тип поддерживает пользовательскую сериализацию, если он реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс. Конструктор сериализации является обязательным и используется для отмены сериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метода. Поскольку конструктор сериализации выделяет и инициализирует объекты, проверки безопасности, которые имеются в обычных конструкторах, также должны присутствовать в конструкторе сериализации. Если вы нарушаете это правило, вызывающие объекты, которые не могли бы создать экземпляр, могут использовать конструктор сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, необходимо защитить конструктор сериализации с помощью требований безопасности, идентичных тем, которые защищают другие конструкторы.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не следует подавлять нарушение правила.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237. Пометьте типы ISerializable с SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>