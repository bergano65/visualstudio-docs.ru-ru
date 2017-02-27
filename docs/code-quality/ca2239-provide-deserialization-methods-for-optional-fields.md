---
title: "CA2239: предоставляйте методы десериализации для необязательных полей | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2239: предоставляйте методы десериализации для необязательных полей
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип имеет поле с атрибутом <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> и не предоставляет методы десериализации события.  
  
## Описание правила  
 Атрибут <xref:System.Runtime.Serialization.OptionalFieldAttribute> не влияет на сериализацию. Поле с таким атрибутом сериализуется.  Однако поле не обрабатывается при десериализации и сохраняет значение по умолчанию, связанное с типом поля.  Для обработки поля в процессе десериализации следует объявлять обработчики событий десериализации.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, добавьте в тип обработчики событий десериализации.  
  
## Отключение предупреждений  
 Можно безопасно отключать предупреждения этого правила, если поле нужно пропустить в процессе десериализации.  
  
## Пример  
 В следующем примере показан тип с необязательным полем и методы обработки событий десериализации.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../Topic/CA2120:%20Secure%20serialization%20constructors.md)