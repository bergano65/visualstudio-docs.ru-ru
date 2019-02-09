---
title: CA1041. Укажите сообщение ObsoleteAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bb8281cb299b9b6ada7470deca82b9158fb323d1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953104"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041. Укажите сообщение ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или член помечен с помощью <xref:System.ObsoleteAttribute?displayProperty=fullName> атрибут, который не поддерживает его <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> указанное свойство.

## <a name="rule-description"></a>Описание правила
 <xref:System.ObsoleteAttribute> используется для пометки устаревшие библиотеки типов и членов. Потребители библиотеки следует избегать использования любого типа или члена, который помечен как устаревший. Это, так как он может не поддерживаться и в конечном итоге будет отсутствовать в более поздних версиях библиотеки. Если тип или член помечен с помощью <xref:System.ObsoleteAttribute> компилируется, <xref:System.ObsoleteAttribute.Message%2A> отображается свойство атрибута. Это предоставляет пользователю сведения об устаревшем типе или члене. Эти сведения обычно содержат как долго устаревший тип или член будет поддерживаться разработчиками и какой компонент для использования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте `message` параметр <xref:System.ObsoleteAttribute> конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, так как <xref:System.ObsoleteAttribute.Message%2A> свойство предоставляет важные сведения о устаревший тип или член.

## <a name="example"></a>Пример
 В следующем примере показано устаревший член, который есть правильно объявленный <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>См. также
 <xref:System.ObsoleteAttribute?displayProperty=fullName>