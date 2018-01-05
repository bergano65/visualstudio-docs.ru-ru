---
title: "CA1717: Только перечисления FlagsAttribute должны иметь имена во множественном числе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 203ee8af0f28f272ece784f086f7aeba7341dfc4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: только перечисления FlagsAttribute должны иметь имена во множественном числе
|||  
|-|-|  
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|  
|CheckId|CA1717|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи перечисления заканчивается на множественном, и перечисления не помечен атрибутом <xref:System.FlagsAttribute?displayProperty=fullName> атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 Согласно правилам именования множественное число имени перечисления указывает, что несколько значений перечисления можно указывать одновременно. <xref:System.FlagsAttribute> Сообщает компилятору, что перечисление должно рассматриваться как битовое поле, которое позволяет побитовых операций над перечисления.  
  
 Если только одновременно можно указать одно значение перечисления, имя перечисления должно быть словом в единственном числе. Например перечисление, определяющее дни недели, могут быть предназначены для использования в приложении, где можно указать несколько дней. Это перечисление должен иметь <xref:System.FlagsAttribute> и может быть вызвана «Дни». Похожее перечисление, которое позволяет указывать только один день не будет иметь атрибут и может быть вызван «Day».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Выбрать имя перечисления словом в единственном числе или добавить <xref:System.FlagsAttribute>.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из правила, если имя заканчивается словом в единственном числе.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1714: имена перечислений флагов должны быть во множественном числе](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Разработка перечислений](/dotnet/standard/design-guidelines/enum)