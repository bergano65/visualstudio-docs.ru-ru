---
title: 'CA1041: Укажите сообщение ObsoleteAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542315"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041. Укажите сообщение ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или член помечается с помощью <xref:System.ObsoleteAttribute?displayProperty=fullName> атрибута, для которого не <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> указано свойство.

## <a name="rule-description"></a>Описание правила
 <xref:System.ObsoleteAttribute>используется для обозначения устаревших типов и членов библиотеки. Потребители библиотек должны избегать использования любого типа или члена, помеченного как устаревший. Это связано с тем, что он может не поддерживаться и в конечном итоге будет удален из более поздних версий библиотеки. При компиляции типа или члена, помеченного с помощью <xref:System.ObsoleteAttribute> , <xref:System.ObsoleteAttribute.Message%2A> отображается свойство атрибута. Это предоставляет пользователю сведения об устаревшем типе или члене. Эти сведения обычно включают в себя, как долго устаревший тип или член будет поддерживаться конструкторами библиотек и предпочтительной заменой для использования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте `message` параметр в <xref:System.ObsoleteAttribute> конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, так как <xref:System.ObsoleteAttribute.Message%2A> свойство предоставляет важные сведения об устаревшем типе или члене.

## <a name="example"></a>Пример
 В следующем примере показан устаревший член, который правильно объявлен <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
