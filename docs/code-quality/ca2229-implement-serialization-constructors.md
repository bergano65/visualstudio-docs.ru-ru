---
title: 'CA2229: Реализация конструкторов сериализации | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04906c737c7581b0b1a0c5a3dcc80407aa35659a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: применяйте конструкторы сериализации
|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейсов, не является делегатом или интерфейс, и одно из следующих условий верно:  
  
-   Тип имеет конструктор, принимающий <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> объекта и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> объекта (сигнатура конструктора сериализации).  
  
-   Тип не запечатан и модификатор доступа для конструктора сериализации не является защищенным (семейство).  
  
-   Тип запечатан и модификатор доступа для конструктора сериализации не является закрытым.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило распространяется на типы, поддерживающие пользовательской сериализации. Тип поддерживает пользовательской сериализации, если он реализует <xref:System.Runtime.Serialization.ISerializable> интерфейса. Конструктор сериализации необходим для десериализации или повторного создания объектов, которые были сериализованы с помощью <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> метод.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации. Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте нарушение правила. Тип не будет десериализуемое и не будет работать в разных сценариях.  
  
## <a name="example"></a>Пример  
 В следующем примере тип, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>