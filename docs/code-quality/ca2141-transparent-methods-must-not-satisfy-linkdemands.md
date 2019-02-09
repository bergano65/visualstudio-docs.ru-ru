---
title: 'CA2141: прозрачные методы не должны удовлетворять требования LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdd8ee4633cdc254bcfc5237391120ef887753da
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907234"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: прозрачные методы не должны удовлетворять требования LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный с точки безопасности метод вызывает метод в сборке, которая не помечен атрибутом <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA), или прозрачный метод безопасности удовлетворяет <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` для типа или метода.

## <a name="rule-description"></a>Описание правила
 Удовлетворение требования LinkDemand является важной операцией безопасности, может привести к непреднамеренному повышению уровня привилегий. Прозрачный код безопасности не должны удовлетворять требования LinkDemand, так как он не распространяются те же требования аудита безопасности, что и критический код безопасности. Прозрачные методы в сборках уровня 1 набор правил безопасности приведет все требования LinkDemand, они удовлетворяют для преобразования в полные требования во время выполнения, что может привести к снижению производительности. В сборках уровня 2 набора правил безопасности прозрачные методы не удастся скомпилировать в компилятор just-in-time (JIT), если они пытаются выполнить удовлетворяет требованию LinkDemand.

 В сборках, использующих безопасность уровня 2, вызывает попытки прозрачного безопасности метод удовлетворяет требованию LinkDemand или вызвать метод в сборке, отличный от APTCA <xref:System.MethodAccessException>; в сборках уровня 1 LinkDemand, становятся полными требованиями.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте доступ к метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибут, или удалите LinkDemand из метода доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере прозрачный метод пытается вызвать метод, который имеет LinkDemand. Это правило срабатывает на этот код.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]