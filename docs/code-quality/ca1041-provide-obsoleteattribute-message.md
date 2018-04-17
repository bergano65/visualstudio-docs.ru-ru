---
title: 'CA1041: Укажите сообщение ObsoleteAttribute | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc851ef4b4ef1cdca9bdb1f9692d3bbc7f0a795c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: укажите сообщение ObsoleteAttribute
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип или член, помечен с помощью <xref:System.ObsoleteAttribute?displayProperty=fullName> атрибут, который не поддерживает его <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> указанное свойство.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.ObsoleteAttribute> используется для пометки устаревшие библиотеки типов и членов. Пользователям библиотек следует избегать использования любого типа или члена, который помечен как устаревший. Это, так как он не поддерживается и в конечном итоге будет удалена из более поздних версиях библиотеки. Если тип или член, помечен с помощью <xref:System.ObsoleteAttribute> компилируется, <xref:System.ObsoleteAttribute.Message%2A> отображаются свойства этого атрибута. Это предоставляет пользователю сведения об устаревшем типе или члене. Эти сведения обычно содержат как долго устаревший тип или член будет поддерживаться разработчиками и какой компонент для использования.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте `message` параметр <xref:System.ObsoleteAttribute> конструктора.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, так как <xref:System.ObsoleteAttribute.Message%2A> свойство предоставляет важные сведения об устаревшем типе или члене.  
  
## <a name="example"></a>Пример  
 В следующем примере показано устаревший член, который имеет правильное объявление <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>