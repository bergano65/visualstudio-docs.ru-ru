---
title: 'CA2120: обеспечьте безопасность конструкторов сериализации'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 123bff32b847342f4081a73abb1d8b899cc0efec
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548508"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: обеспечьте безопасность конструкторов сериализации

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не является делегатом или интерфейс и объявлен в сборке, которая позволяет частично доверенным вызывающим объектам. Тип имеет конструктор, принимающий <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объекта и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> объекта (сигнатура конструктора сериализации). Этот конструктор не защищен проверкой безопасности, но один или несколько обычных конструкторов в типе защищена.

## <a name="rule-description"></a>Описание правила
 Это правило относится к типы, поддерживающие пользовательской сериализации. Тип поддерживает пользовательской сериализации, если он реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс. Конструктор сериализации является обязательным и используется для десериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод. Поскольку конструктор сериализации выделяет и инициализирует объекты, проверки безопасности, которые присутствуют в обычных конструкторов также должны присутствовать на конструктор сериализации. При нарушении этого правила, вызывающих объектов, которые не в противном случае может создать экземпляр может использовать конструктор сериализации для этого.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, Защитите конструктор сериализации с помощью требований безопасности, которые идентичны для защиты других конструкторов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте нарушение правила.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>