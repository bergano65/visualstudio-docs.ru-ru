---
title: 'CA1714: перечисления flags должны иметь имена во множественном числе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548191"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714. У перечислений флагов должны быть имена во множественном числе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Общедоступное перечисление имеет <xref:System.FlagsAttribute?displayProperty=fullName> и его имя не оканчивается на ".

## <a name="rule-description"></a>Описание правила
 Типы, помеченные с помощью <xref:System.FlagsAttribute> , имеют имена, которые являются во множественном числе, так как атрибут указывает, что может быть указано более одного значения. Например, перечисление, определяющее дни недели, может быть предназначено для использования в приложении, где можно указать несколько дней. Это перечисление должно содержать <xref:System.FlagsAttribute> и может называться "Days". Аналогичное перечисление, которое позволяет указать только один день, не будет иметь атрибута и может называться "Day".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Сделайте имя перечисления словом множественного числа или удалите <xref:System.FlagsAttribute> атрибут, если не следует одновременно указывать несколько значений перечисления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно подавлять нарушение, если имя является словом во множественном числе, но не заканчивается на ". Например, если перечисление с несколькими днями, описанное ранее, называлось "Дайсофсевик", это нарушает логику правила, но не его намерение. Такие нарушения следует подавлять.

## <a name="related-rules"></a>Связанные правила
 [CA1027. Пометьте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также:
 <xref:System.FlagsAttribute?displayProperty=fullName>[Конструктор перечислений](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
