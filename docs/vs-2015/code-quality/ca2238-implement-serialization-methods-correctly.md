---
title: 'CA2238: следует Правильно реализовывать методы сериализации | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 772127c7472d9b1204953493188ba405c252dbb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568722"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: следует правильно реализовывать методы сериализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio 2017, см. в разделе [CA2238 следует: правильно реализовывать методы сериализации](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly) на сайте docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое, если метод является видимым извне.<br /><br /> Не критическое, если метод не видимый за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Метод, обрабатывающий событие сериализации, не имеет правильной сигнатуры, типа возвращаемого значения или отображения.  
  
## <a name="rule-description"></a>Описание правила  
 Метод назначается обработчику событий сериализации, применив один из следующих атрибутов сериализации события:  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
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
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: помечайте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)

