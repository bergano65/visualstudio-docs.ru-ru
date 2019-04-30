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
ms.openlocfilehash: 2fdf92eae202f1ebb80b88e28307e7dacfbc0a39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542394"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126. Для требований ссылок на тип необходимы требования наследования

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый незапечатанный тип защищен требованием ссылки, имеет переопределяемый метод, и ни тип, ни метод защищен требованием наследования.

## <a name="rule-description"></a>Описание правила
 Запрос ссылки на метод или его объявляющий тип требует немедленного вызывающему объекту метода, указанное разрешение. Требование наследования в методе требует метод переопределения для указанного разрешения. Требования наследования в типе требуется для указанное разрешение производного класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, безопасность типа или метода с помощью требования наследования для те же разрешения, как требование связывания.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2108: Проверьте объявляемые параметры безопасности типов значений](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Не используйте косвенное представление методов с запросами компоновки](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Компоновки переопределения должны быть идентичны базовым](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>См. также

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Требования связывания](/dotnet/framework/misc/link-demands)