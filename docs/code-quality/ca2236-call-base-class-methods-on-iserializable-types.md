---
title: "CA2236: вызывайте методы базового класса для типов ISerializable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2236: вызывайте методы базового класса для типов ISerializable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип происходит от типа, реализующего интерфейс <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, при этом выполняется одно из следующих условий:  
  
-   Тип реализует конструктор сериализации, то есть сигнатурой параметров <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, но не вызывает конструктор сериализации базового типа.  
  
-   Тип реализует метод <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>, но не вызывает метод <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> базового типа.  
  
## Описание правила  
 В настраиваемом процессе сериализации тип реализует метод <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> для сериализации своих полей и конструктор сериализации для отмены сериализации полей.  Если тип происходит от типа, реализующего интерфейс <xref:System.Runtime.Serialization.ISerializable>, то нужно вызывать метод базового типа <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> и конструктор сериализации для сериализации и отмены сериализации полей базового типа.  В противном сериализация и отмена сериализации типа не будут выполнены правильно.  Обратите внимание, что если в производном типе не добавляются никакие новые поля, тип не должен реализовывать метод <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> или конструктор сериализации и не должен вызывать эквиваленты базового типа.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, вызовите метод базового типа <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> или конструктор сериализации из соответствующего метода типа или конструктора.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан производный тип, соответствующий правилу благодаря вызову конструктора сериализации и метода базового класса <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Связанные правила  
 [CA2240: правильно реализуйте ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../Topic/CA2120:%20Secure%20serialization%20constructors.md)