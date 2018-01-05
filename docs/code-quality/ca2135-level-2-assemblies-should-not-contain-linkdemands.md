---
title: "CA2135: Сборки уровня 2 не должны содержать LinkDemands | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea4d0adf3573410c9f8a25e6b5d3abf2615c8ad3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: сборки уровня 2 не должны содержать требования LinkDemand
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 С помощью класса или члена класса <xref:System.Security.Permissions.SecurityAction> в приложении, которое используется безопасность уровня 2.  
  
## <a name="rule-description"></a>Описание правила  
 Требования LinkDemand являются устаревшими в наборе правил безопасности уровня 2. Вместо использования требования LinkDemand для обеспечения безопасности во время компиляции just-in-time (JIT), пометьте методы, типы и поля с <xref:System.Security.SecurityCriticalAttribute> атрибута.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите <xref:System.Security.Permissions.SecurityAction> и пометить этот тип или член с <xref:System.Security.SecurityCriticalAttribute> атрибута.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере <xref:System.Security.Permissions.SecurityAction> должны быть удалены, и метод помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]