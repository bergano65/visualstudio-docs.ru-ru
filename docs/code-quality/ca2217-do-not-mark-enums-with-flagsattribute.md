---
title: "CA2217: не следует помечать перечисления атрибутом FlagsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2217: не следует помечать перечисления атрибутом FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Видимое извне перечисление помечено атрибутом <xref:System.FlagsAttribute> и имеет одно или несколько значений, которые не являются степенями двух или комбинацией других определенных значений в перечислении.  
  
## Описание правила  
 Перечисление должно иметь атрибут <xref:System.FlagsAttribute>, только если каждое значение, определенное в перечислении, является степенью двух или комбинацией определенных значений.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут <xref:System.FlagsAttribute> из перечисления.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показано перечисление "Color", которое содержит значение 3, не являющееся степенью двух или сочетанием других определенных значений.  Перечисление "Color" не должно быть помечено атрибутом <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## Пример  
 В следующем примере показано перечисление "Days", которое соответствует требованиям для пометки атрибутом System.FlagsAttribute.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## Связанные правила  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## См. также  
 <xref:System.FlagsAttribute?displayProperty=fullName>