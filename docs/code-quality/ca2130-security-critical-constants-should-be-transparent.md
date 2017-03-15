---
title: "CA2130: константы критической безопасности должны быть прозрачными | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2130: константы критической безопасности должны быть прозрачными
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Константное поле или элемент перечисления помечается атрибутом <xref:System.Security.SecurityCriticalAttribute>.  
  
## Описание правила  
 Принудительная прозрачность не применяется для постоянных значений, чтобы во время выполнения не требовалась подстановка значений.  Константные поля должны быть прозрачными для системы безопасности, чтобы анализаторы кода не предполагали, что прозрачный для системы безопасности код не может получить доступ к константе.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут SecurityCritical из поля или значения.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующих примерах данное предупреждение вызывается значением перечисления `EnumWithCriticalValues.CriticalEnumValue` и константой `CriticalConstant`.  Чтобы устранить проблемы, удалите атрибут \[`SecurityCritical`\], чтобы сделать их прозрачными для безопасности.  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]