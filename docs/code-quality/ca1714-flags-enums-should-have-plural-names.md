---
title: 'CA1714: Имена перечислений флагов должны быть во множественном числе | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5dc35718a20743ce6ed1502dbd1d9ed3c8a626e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: имена перечислений флагов должны быть во множественном числе
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытое перечисление содержит <xref:System.FlagsAttribute?displayProperty=fullName> и его имя не заканчивается в ".  
  
## <a name="rule-description"></a>Описание правила  
 Типы, помеченные <xref:System.FlagsAttribute> имеют имена, которые используются во множественном числе, поскольку данный атрибут указывает, что можно указать более одного значения. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должен иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указывать только один день не будет иметь атрибут и может быть вызван «Day».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Сделайте имя перечисления множественном, или удалите <xref:System.FlagsAttribute> атрибута, если одновременно не следует указывать несколько значений перечисления.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Безопасно можно отключить, если имя указано во множественном, но не заканчивается на ". Например если перечисление несколько дней, которое было описано ранее были названы «DaysOfTheWeek», это приведет к нарушению логике правила, но не его назначение. Подобные нарушения следует отключать.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Разработка перечислений](/dotnet/standard/design-guidelines/enum)