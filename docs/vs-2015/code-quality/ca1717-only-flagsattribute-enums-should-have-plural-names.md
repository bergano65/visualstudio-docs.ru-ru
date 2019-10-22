---
title: 'CA1717: только перечисления FlagsAttribute должны иметь имена во множественном числе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669082"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: только перечисления FlagsAttribute должны иметь имена во множественном числе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя перечисления, видимого извне, заканчивается в слове во множественном числе, а перечисление не помечено атрибутом <xref:System.FlagsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Соглашения об именовании определяют, что имя перечисления во множественном числе указывает, что можно одновременно указать несколько значений перечисления. @No__t_0 сообщает компиляторам, что перечисление должно обрабатываться как битовое поле, которое включает побитовые операции перечисления.

 Если в каждый момент времени может быть указано только одно значение перечисления, то имя перечисления должно быть словом в единственном числе. Например, перечисление, определяющее дни недели, может быть предназначено для использования в приложении, где можно указать несколько дней. Это перечисление должно иметь <xref:System.FlagsAttribute> и может называться "Days". Аналогичное перечисление, которое позволяет указать только один день, не будет иметь атрибута и может называться "Day".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает время, необходимое для изучения новой библиотеки программного обеспечения, и повышает уверенность клиентов в том, что библиотека была разработана пользователями, обладающими опытом в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Сделайте имя перечисления словом в единственном числе или добавьте <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из правила, если имя заканчивается в единственном слове.

## <a name="related-rules"></a>Связанные правила
 [CA1714: имена перечислений флагов должны быть во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также раздел
 [конструктор Перечислений](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545) <xref:System.FlagsAttribute?displayProperty=fullName>
