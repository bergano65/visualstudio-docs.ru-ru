---
title: CA2126. Требования связывания типов должны требовать наследования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7bc7c9639d12cc6981c91320104a1565bb1f94e9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609033"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126. Для требований ссылок на тип необходимы требования наследования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
 Открытый незапечатанный тип защищен с помощью запроса компоновки, имеет переопределяемый метод, и ни тип, ни метод не защищены требованием наследования.

## <a name="rule-description"></a>Описание правила
 Требование ссылки на метод или его объявляющий тип требует, чтобы непосредственно вызывающий объект метода имел указанное разрешение. Требование наследования для метода требует наличия указанного разрешения в переопределяющем методе. Требование наследования для типа требует, чтобы производный класс имел указанное разрешение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, обеспечьте безопасность типа или метода с требованием наследования для того же разрешения, что и для запроса компоновки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2108: Проверьте декларативную безопасность типов значений ](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Защищенные типы не должны предоставлять поля ](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Не следует косвенно предоставлять методы с запросами компоновки ](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Запросы на переопределение ссылок должны быть идентичны базовым ](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>См. также
 [Рекомендации по безопасному написанию кода](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [требования к запросам](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) на [требование связывания](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [требования](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)
