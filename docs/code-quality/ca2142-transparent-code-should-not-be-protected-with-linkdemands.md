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
ms.openlocfilehash: ab0f6aaae97a510b0521e10ad607a86988c345a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232085"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142. Прозрачный код не должен быть защищен проверками LinkDemands

|||
|-|-|
|TypeName|транспарентмесодсшаулднотбепротектедвислинкдемандс|
|CheckId|CA2142|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Для прозрачного метода требуется <xref:System.Security.Permissions.SecurityAction> или другое требование безопасности.

## <a name="rule-description"></a>Описание правила
Это правило срабатывает для прозрачных методов, для доступа к которым требуется LinkDemand. Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Поскольку прозрачные методы должны быть нейтральными к безопасности, они не должны принимать никаких решений в отношении безопасности. Кроме того, безопасный критически важный код, который принимает решения по безопасности, не должен полагаться на прозрачный код, чтобы ранее было сделано такое решение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите требование компоновки для прозрачного метода или пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом, если он выполняет проверки безопасности, например требования безопасности.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере правило срабатывает для метода, так как метод является прозрачным и помечен с помощью LinkDemand <xref:System.Security.PermissionSet> , который <xref:System.Security.Permissions.SecurityAction>содержит.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Для этого правила отключать вывод предупреждений не следует.