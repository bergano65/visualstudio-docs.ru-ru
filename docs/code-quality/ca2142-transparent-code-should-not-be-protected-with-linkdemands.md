---
title: 'CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand'
ms.date: 11/04/2016
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
ms.openlocfilehash: 58f0c934c029c65a07fd0e89a5822dbbe0849428
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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
 Это правило срабатывает для прозрачных методов, для доступа к которым требуется LinkDemand. Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Так как прозрачные методы должны быть нейтральной безопасности, они не должны принимать решений по безопасности. Кроме того безопасном критического кода, который принятия решений по безопасности, не должен полагаться на прозрачный код, который ранее принимал такое решение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите требование компоновки прозрачного метода или пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> проверки атрибута, если он выполняет безопасности, такие как требования безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере это правило срабатывает для метода, так как метод является прозрачным и помечается с помощью LinkDemand <xref:System.Security.PermissionSet> , содержащий <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Для этого правила отключать вывод предупреждений не следует.