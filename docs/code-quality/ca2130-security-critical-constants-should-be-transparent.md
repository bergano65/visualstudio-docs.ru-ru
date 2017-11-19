---
title: "CA2130: Константы критической безопасности должны быть прозрачными | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9975acd53976b1668e158fd3e906c669a0f5ed49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: константы критической безопасности должны быть прозрачными
|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Константного поля или член перечисления помечается <xref:System.Security.SecurityCriticalAttribute>.  
  
## <a name="rule-description"></a>Описание правила  
 Принудительная прозрачность не применяется для постоянных значений, чтобы во время выполнения не требовалась подстановка значений. Константные поля должны быть прозрачными для системы безопасности, чтобы анализаторы кода не предполагали, что прозрачный для системы безопасности код не может получить доступ к константе.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут SecurityCritical из поля или значения.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующих примерах, значение перечисления `EnumWithCriticalValues.CriticalEnumValue` с константой `CriticalConstant` вызвать данное предупреждение. Чтобы устранить проблемы, удалите [`SecurityCritical`] атрибута, чтобы сделать их безопасности прозрачным.  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]