---
title: "CA1028: хранилище перечислений должно иметь тип Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1028: хранилище перечислений должно иметь тип Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Базовый тип открытого перечисления отличен от <xref:System.Int32?displayProperty=fullName>.  
  
## Описание правила  
 Перечисление является типом значения, которое определяет набор связанных именованных констант.  По умолчанию для хранения значения константы используется тип данных <xref:System.Int32?displayProperty=fullName>.  Этот базовый тип можно изменить, но этого не требуется и в большинстве случаев это не рекомендуется.  Обратите внимание, что при использовании более мелкого типа данных, чем <xref:System.Int32>, прирост производительности весьма незначителен.  Если невозможно использовать тип данных по умолчанию, следует использовать один из встроенных типов, совместимых с CLS \(<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> или <xref:System.Int64>\), чтобы убедиться, что все значения перечисления могут быть представлены на языках программирования, совместимых с CLS.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте тип <xref:System.Int32>, если не возникают проблемы с размером или совместимостью.  В случаях, когда размер <xref:System.Int32> недостаточен для хранения значений, используйте <xref:System.Int64>.  Если в целях обратной совместимости требуется более мелкий тип данных, используйте <xref:System.Byte> или <xref:System.Int16>.  
  
## Отключение предупреждений  
 Предупреждения этого правила можно отключать только в случае, если другой тип данных используется в целях обратной совместимости.  В приложениях обычно не возникает проблем из\-за нарушения этого правила.  В библиотеках, где требуется обеспечить взаимодействие языков, нарушение этого правила может затруднить работу пользователей.  
  
## Пример нарушения  
  
### Описание  
 В следующем примере показаны два перечисления, не использующие рекомендованный базовый тип данных.  
  
### Код  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Пример исправления нарушения  
  
### Описание  
 В следующем примере нарушение устраняется путем изменения базового типа данных на <xref:System.Int32>.  
  
### Код  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Связанные правила  
 [CA1008: перечисляемые типы должны иметь нулевое значение](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## См. также  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>