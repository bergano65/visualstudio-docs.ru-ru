---
title: "CA2235: помечайте все несериализуемые поля | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2235: помечайте все несериализуемые поля
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.  
  
## Описание правила  
 Сериализуемый тип — это тип, помеченный атрибутом <xref:System.SerializableAttribute?displayProperty=fullName>.  При сериализации этого типа возникает исключение <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName>, если тип содержит поле экземпляра несериализуемого типа.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, примените атрибут <xref:System.NonSerializedAttribute?displayProperty=fullName> к несериализуемому полю.  
  
## Отключение предупреждений  
 Отключать предупреждения этого правила следует только при объявлении типа <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>, позволяющего сериализовать и десериализовать экземпляры поля.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило, и тип, удовлетворяющий ему.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../Topic/CA2120:%20Secure%20serialization%20constructors.md)