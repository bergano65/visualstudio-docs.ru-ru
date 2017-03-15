---
title: "CA2229: применяйте конструкторы сериализации | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2229: применяйте конструкторы сериализации
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип реализует интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> , не является делегатом или интерфейсом и выполняется одно из следующих условий:  
  
-   Тип не имеет конструктора, принимающего объект <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> и <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(подпись конструктора сериализации\).  
  
-   Тип незапечатан и модификатор доступа для конструктора сериализации не является защищенным \(семейство\).  
  
-   Тип запечатан и модификатор доступа для конструктора сериализации не является закрытым.  
  
## Описание правила  
 Данное правило распространяется на типы, поддерживающие пользовательскую сериализацию.  Чтобы поддерживать пользовательскую сериализацию, тип должен реализовывать интерфейс <xref:System.Runtime.Serialization.ISerializable>.  Конструктор сериализации необходим для десериализации, то есть для воссоздания объектов, которые были сериализованы методом <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации.  Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.  
  
## Отключение предупреждений  
 Не следует отключать предупреждения о нарушении этого правила.  Тип не будет десериализуемым и не будет работать в большинстве случаев.  
  
## Пример  
 В следующем примере демонстрируется тип, соответствующий правилу.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Связанные правила  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## См. также  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>