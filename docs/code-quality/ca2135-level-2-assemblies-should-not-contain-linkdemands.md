---
title: 'CA2135: сборки уровня 2 не должны содержать требования LinkDemand'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d41310ba5c6e52add891a4a8d034c774f9f74d2
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549612"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: сборки уровня 2 не должны содержать требования LinkDemand
|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 С помощью класса или члена класса <xref:System.Security.Permissions.SecurityAction> в приложении, которое использует безопасность уровня 2.

## <a name="rule-description"></a>Описание правила
 Требования LinkDemand являются устаревшими в наборе правил безопасности уровня 2. Вместо использования требования LinkDemand для обеспечения безопасности во время компиляции just-in-time (JIT), пометьте методы, типы и поля с <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите <xref:System.Security.Permissions.SecurityAction> и пометить тип или член с <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере <xref:System.Security.Permissions.SecurityAction> должны быть удалены, и метод помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]