---
title: "CA1714: Имена перечислений флагов должны быть во множественном числе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82f5e18b838e6f6c0696359a9d88ba3350e636ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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