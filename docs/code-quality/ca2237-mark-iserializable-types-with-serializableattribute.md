---
title: 'CA2237: Пометьте типы ISerializable атрибутом SerializableAttribute | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9b4c0d05e972b4cf9a84677ccbc7d15d117c3f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: пометьте типы ISerializable атрибутом SerializableAttribute
|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Видимый извне тип реализует <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> интерфейс и тип не помечен атрибутом <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. Правило не учитывает производных типов, базовый тип которого не является сериализуемым.  
  
## <a name="rule-description"></a>Описание правила  
 Распознаваемых общеязыковая среда выполнения как сериализуемый, типы должны быть отмечены <xref:System.SerializableAttribute> атрибута, даже если тип использует пользовательскую процедуру сериализации посредством реализации <xref:System.Runtime.Serialization.ISerializable> интерфейса.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, примените <xref:System.SerializableAttribute> к типу атрибут.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила для классов исключений, так как они должны быть сериализуемыми, для правильной работы в доменах приложений.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило. Раскомментируйте <xref:System.SerializableAttribute> атрибут строки в соответствии с правилом.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)