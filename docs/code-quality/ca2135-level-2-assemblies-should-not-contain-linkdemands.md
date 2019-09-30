---
title: CA2135. Сборки уровня 2 не должны содержать LinkDemands
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b9e7cb0eba06b00b30c2b7d00fac78206d222f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232246"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135. Сборки уровня 2 не должны содержать LinkDemands

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Класс или член класса использует <xref:System.Security.Permissions.SecurityAction> в приложении, использующем безопасность уровня 2.

## <a name="rule-description"></a>Описание правила
Требования LinkDemand являются устаревшими в наборе правил безопасности уровня 2. Вместо использования LinkDemand для обеспечения безопасности во время JIT-компиляции пометьте методы, типы и поля <xref:System.Security.SecurityCriticalAttribute> атрибутом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите <xref:System.Security.Permissions.SecurityAction> и пометьте тип или член <xref:System.Security.SecurityCriticalAttribute> атрибутом.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере <xref:System.Security.Permissions.SecurityAction> следует удалить и метод, помеченный <xref:System.Security.SecurityCriticalAttribute> атрибутом.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]