---
title: 'CA1717: Только перечисления FlagsAttribute должны иметь имена во множественном числе | Документация Майкрософт'
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
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fbaa220d39f72900dbf03d238a45fc988b65e6b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592297"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: только перечисления FlagsAttribute должны иметь имена во множественном числе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1717: перечисления только FlagsAttribute должны иметь имена во множественном числе](https://docs.microsoft.com/visualstudio/code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names).

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя видимого перечисления заканчивается на слова во множественном числе и перечисления не помечен атрибутом <xref:System.FlagsAttribute?displayProperty=fullName> атрибута.

## <a name="rule-description"></a>Описание правила
 Соглашения об именовании диктовать, что множественное число имени перечисления указывает, что более одного значения перечисления могут быть заданы одновременно. <xref:System.FlagsAttribute> Сообщает компилятору, что перечисление должно рассматриваться как битовое поле, которое позволяет побитовых операций над перечисления.

 Если только одно значение перечисления можно указать за раз, имя перечисления должно быть словом в единственном числе. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должны иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указать только один день не атрибут и не может быть вызван «Day».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Формируемая перечисления словом в единственном числе, или добавьте <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из правила, если имя функции оканчивается словом в единственном числе.

## <a name="related-rules"></a>Связанные правила
 [CA1714: имена перечислений флагов должны быть во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также
 <xref:System.FlagsAttribute?displayProperty=fullName> [Разработка перечислений](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)



