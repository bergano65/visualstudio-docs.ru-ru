---
title: 'CA1712: Не добавляйте префикс в виде значения перечисления с именем типа | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5858e29e680d33f3603ccc5a44bdf07d797b625
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: не добавляйте имя типа перед перечисляемыми значениями
|||  
|-|-|  
|TypeName|DoNotPrefixEnumValuesWithTypeName|  
|CheckId|CA1712|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Перечисление содержит член, имя которых начинается с именем типа перечисления.  
  
## <a name="rule-description"></a>Описание правила  
 Имена членов перечисления не имеют префикс с именем типа, так как ожидается, сведения о типе предоставляются средствами разработки.  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает время, которое требуется для изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите префикс имени типа из имени члена перечисления.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано перечисление с неправильным именем следуют исправленную версию.  
  
 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1711: идентификаторы не должны иметь неверных суффиксов](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Enum?displayProperty=fullName>