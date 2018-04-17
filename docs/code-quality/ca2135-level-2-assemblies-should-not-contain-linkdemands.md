---
title: 'CA2135: Сборки уровня 2 не должны содержать LinkDemands | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0be276db088e30a71e40905423c5c88a5b714d43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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