---
title: CA2126. Для требований ссылок на тип необходимы требования наследования
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920754"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126. Для требований ссылок на тип необходимы требования наследования

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Открытый незапечатанный тип защищен с помощью запроса компоновки, имеет переопределяемый метод, и ни тип, ни метод не защищены требованием наследования.

## <a name="rule-description"></a>Описание правила
Требование ссылки на метод или его объявляющий тип требует, чтобы непосредственно вызывающий объект метода имел указанное разрешение. Требование наследования для метода требует наличия указанного разрешения в переопределяющем методе. Требование наследования для типа требует, чтобы производный класс имел указанное разрешение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, обеспечьте безопасность типа или метода с требованием наследования для того же разрешения, что и для запроса компоновки.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2108: Проверка декларативной безопасности для типов значений](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122 Не следует косвенно предоставлять методы с запросами компоновки](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123 Запросы на переопределение ссылок должны быть идентичны базовым](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>См. также

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Требования связывания](/dotnet/framework/misc/link-demands)