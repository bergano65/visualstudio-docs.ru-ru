---
title: 'CA2120: Обеспечьте безопасность конструкторов сериализации | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 0032e2a20c90d11db33c94397e8c8b8cadbd86db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: обеспечьте безопасность конструкторов сериализации
|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс, не является делегатом или интерфейс и объявлен в сборке, которая позволяет частично доверенным вызывающим объектам. Тип имеет конструктор, принимающий <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объекта и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> объекта (сигнатура конструктора сериализации). Этот конструктор не защищен проверкой безопасности, однако один или несколько обычных конструкторов этого типа защищена.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило распространяется на типы, поддерживающие пользовательской сериализации. Тип поддерживает пользовательской сериализации, если он реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейса. Конструктор сериализации является обязательным и используется для отмены сериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод. Поскольку конструктор сериализации выделяет и инициализирует объекты, проверки безопасности, применяемые для обычных конструкторов, также должны присутствовать на конструктор сериализации. Если вы нарушение этого правила, вызывающих объектов, которые не в противном случае может создать экземпляр использовать конструктор сериализации для этого.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, Защитите конструктор сериализации с помощью требований безопасности, которые идентичны для защиты других конструкторов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте нарушение правила.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>