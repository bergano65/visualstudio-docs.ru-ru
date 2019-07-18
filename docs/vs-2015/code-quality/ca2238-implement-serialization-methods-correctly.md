---
title: CA2238. Правильно реализовывать методы сериализации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cff617adf2b31ef773de3bc41db7245346795bee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142381"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238. Правильно реализуйте методы сериализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio, см. в разделе [CA2238 следует: Правильно реализовывать методы сериализации](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое, если метод является видимым извне.<br /><br /> Non критическое, если метод не видимый за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Метод, обрабатывающий событие сериализации, не имеет правильной сигнатуры, типа возвращаемого значения или отображения.  
  
## <a name="rule-description"></a>Описание правила  
 Метод назначается обработчику событий сериализации, применив один из следующих атрибутов сериализации события:  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Обработчики событий сериализации принимать один параметр типа <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, возвращают `void`и иметь `private` видимости.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте подпись, тип возвращаемого значения или видимость обработчика событий сериализации.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает правильное объявление сериализации обработчики событий.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2236: Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Предоставляйте методы десериализации для необязательных полей](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)
