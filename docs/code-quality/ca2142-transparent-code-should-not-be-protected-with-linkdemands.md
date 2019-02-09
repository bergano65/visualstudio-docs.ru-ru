---
title: CA2142. Прозрачный код не должен быть защищен проверками LinkDemands
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b05228ef22dee20506b728164d22976feb662ae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945993"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142. Прозрачный код не должен быть защищен проверками LinkDemands

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