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
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668328"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: укажите сообщение ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или член помечается с помощью <xref:System.ObsoleteAttribute?displayProperty=fullName> атрибута, для которого не задано свойство <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.ObsoleteAttribute> используется для обозначения устаревших типов и членов библиотеки. Потребители библиотек должны избегать использования любого типа или члена, помеченного как устаревший. Это связано с тем, что он может не поддерживаться и в конечном итоге будет удален из более поздних версий библиотеки. При компиляции типа или члена, помеченного с помощью <xref:System.ObsoleteAttribute>, отображается свойство <xref:System.ObsoleteAttribute.Message%2A> атрибута. Это предоставляет пользователю сведения об устаревшем типе или члене. Эти сведения обычно включают в себя, как долго устаревший тип или член будет поддерживаться конструкторами библиотек и предпочтительной заменой для использования.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте параметр `message` в конструктор <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, так как свойство <xref:System.ObsoleteAttribute.Message%2A> предоставляет важные сведения об устаревшем типе или члене.

## <a name="example"></a>Пример
 В следующем примере показан устаревший член с правильно объявленным <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>См. также раздел
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
