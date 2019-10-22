---
title: 'CA2120: безопасные конструкторы сериализации | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b734a5de257273312e5125c5f481ff889cd33e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664757"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: обеспечьте безопасность конструкторов сериализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип реализует интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, не является делегатом или интерфейсом, и объявляется в сборке, которая допускает частично доверенные вызывающие объекты. Тип имеет конструктор, принимающий объект <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> и объект <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (сигнатура конструктора сериализации). Этот конструктор не защищен проверкой безопасности, но один или несколько обычных конструкторов в типе защищены.

## <a name="rule-description"></a>Описание правила
 Это правило относится к типам, поддерживающим пользовательскую сериализацию. Тип поддерживает пользовательскую сериализацию, если он реализует интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>. Конструктор сериализации является обязательным и используется для отмены сериализации или повторного создания объектов, которые были сериализованы с помощью метода <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>. Поскольку конструктор сериализации выделяет и инициализирует объекты, проверки безопасности, которые имеются в обычных конструкторах, также должны присутствовать в конструкторе сериализации. Если вы нарушаете это правило, вызывающие объекты, которые не могли бы создать экземпляр, могут использовать конструктор сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, необходимо защитить конструктор сериализации с помощью требований безопасности, идентичных тем, которые защищают другие конструкторы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует подавлять нарушение правила.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
