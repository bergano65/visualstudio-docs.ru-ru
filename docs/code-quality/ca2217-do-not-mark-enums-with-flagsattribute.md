---
title: 'CA2217: Не следует помечать перечисления атрибутом FlagsAttribute | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a2cdfcf4014d00ca2d975a04a8bb81191a717e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: не следует помечать перечисления атрибутом FlagsAttribute
|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Видимый для внешнего кода перечисление помечено атрибутом <xref:System.FlagsAttribute> и он имеет один или несколько значений, не являющиеся степенями двух или сочетание другой определенных значений в перечислении.  
  
## <a name="rule-description"></a>Описание правила  
 Перечисление должно иметь <xref:System.FlagsAttribute> присутствуют, только в том случае, если каждое значение, определенное в перечислении является степенью двух или сочетание определенных значений.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите <xref:System.FlagsAttribute> из перечисления.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано перечисление цвета, содержащий значение 3, что не является степенью двух ни ни сочетание любых определенных значений. Не следует помечать перечисления цвет с <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано перечисления дней, которое отвечает требованиям для пометки атрибутом System.FlagsAttribute.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.FlagsAttribute?displayProperty=fullName>