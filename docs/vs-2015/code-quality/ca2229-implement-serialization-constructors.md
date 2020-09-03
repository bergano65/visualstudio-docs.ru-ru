---
title: 'CA2229: реализация конструкторов сериализации | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540495"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229. Реализуйте конструкторы сериализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не является делегатом или интерфейсом, и одно из следующих условий имеет значение true:

- Тип не имеет конструктора, принимающего <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объект и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> объект (сигнатура конструктора сериализации).

- Тип является незапечатанным, а модификатор доступа для его конструктора сериализации не защищен (Family).

- Тип запечатан, а модификатор доступа для его конструктора сериализации не является закрытым.

## <a name="rule-description"></a>Описание правила
 Это правило относится к типам, поддерживающим пользовательскую сериализацию. Тип поддерживает пользовательскую сериализацию, если он реализует <xref:System.Runtime.Serialization.ISerializable> интерфейс. Конструктор сериализации необходим для десериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации. Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует подавлять нарушение правила. Тип не будет десериализуемым и не будет работать во многих сценариях.

## <a name="example"></a>Пример
 В следующем примере показан тип, удовлетворяющий правилу.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также:
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
