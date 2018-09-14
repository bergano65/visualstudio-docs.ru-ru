---
title: 'CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 527086fa2b17de0330b394a7041232312f3b1719
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547220"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand
|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод требует <xref:System.Security.Permissions.SecurityAction> или другие требования безопасности.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для прозрачных методов, которые требуется LinkDemand для доступа к ним. Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Так как прозрачные методы должны быть нейтрального безопасности, они не должны принимать какие-либо решения безопасности. Кроме того код safe critical, который принятия решений по безопасности, не должен полагаться на прозрачный код, ранее были внесены такие решения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите требование связывания прозрачного метода или пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> проверяет атрибут, если он выполняет безопасности, такие как требования безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере, это правило применяется для метода, так как метод является прозрачным, а также помечен с помощью LinkDemand <xref:System.Security.PermissionSet> , содержащий <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Для этого правила отключать вывод предупреждений не следует.