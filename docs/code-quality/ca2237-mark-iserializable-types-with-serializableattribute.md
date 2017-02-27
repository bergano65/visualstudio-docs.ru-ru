---
title: "CA2237: пометьте типы ISerializable атрибутом SerializableAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237: пометьте типы ISerializable атрибутом SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Доступный для внешнего кода тип реализует интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, однако тип не помечен атрибутом <xref:System.SerializableAttribute?displayProperty=fullName>.  Согласно данному правилу, типы, производные от несериализуемого базового типа, пропускаются.  
  
## Описание правила  
 Чтобы среда CLR распознавала тип как сериализуемый, он должен быть помечен атрибутом <xref:System.SerializableAttribute> даже в том случае, если тип использует пользовательскую процедуру сериализации посредством реализации интерфейса <xref:System.Runtime.Serialization.ISerializable>.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, примените к типу атрибут <xref:System.SerializableAttribute>.  
  
## Отключение предупреждений  
 Не следует отключать предупреждение о нарушении данного правила для классов исключений, поскольку дли правильной работы в доменах приложений эти классы должны быть сериализуемыми.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  Чтобы устранить нарушение правила, снимите метку комментария со строки атрибута <xref:System.SerializableAttribute>.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../Topic/CA2120:%20Secure%20serialization%20constructors.md)