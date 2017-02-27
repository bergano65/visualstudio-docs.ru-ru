---
title: "CA2238: следует правильно реализовывать методы сериализации | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementSerializationMethodsCorrectly"
  - "CA2238"
helpviewer_keywords: 
  - "CA2238"
  - "ImplementSerializationMethodsCorrectly"
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2238: следует правильно реализовывать методы сериализации
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое, если метод отображается за пределами сборки.<br /><br /> Не критическое, если метод не отображается за пределами сборки.|  
  
## Причина  
 Метод, обрабатывающий событие сериализации, не имеет правильной сигнатуры, возвращаемого типа или отображения.  
  
## Описание правила  
 Метод назначается обработчику событий сериализации путем применения одного из следующих атрибутов события сериализации.  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Обработчики событий сериализации принимают один параметр типа <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, возвращают `void` и имеют отображение `private`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте подпись, возвращаемый тип или отображение обработчика событий сриализации.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показано правильное объявление обработчиков событий сериализации.  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-cs[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../Topic/CA2120:%20Secure%20serialization%20constructors.md)