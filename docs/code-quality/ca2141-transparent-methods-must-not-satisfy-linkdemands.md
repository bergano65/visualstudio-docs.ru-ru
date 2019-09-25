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
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232122"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: прозрачные методы не должны удовлетворять требования LinkDemand

|||
|-|-|
|TypeName|транспарентмесодсмустнотсатисфилинкдемандс|
|CheckId|CA2141|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Прозрачный с помощью безопасности метод вызывает метод в сборке, которая не помечена <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибутом (APTCA), или прозрачный `.LinkDemand` для безопасности метод удовлетворяет <xref:System.Security.Permissions.SecurityAction> типу или методу.

## <a name="rule-description"></a>Описание правила
Соблюдение требований LinkDemand — это операция, учитывающая безопасность, которая может привести к непреднамеренному повышению привилегий. Прозрачный для системы безопасности код не должен удовлетворять требования LinkDemand, так как он не подчиняется тем же требованиям аудита безопасности, что и критически важный для безопасности код. Прозрачные методы в сборках уровня 1 набора правил безопасности приведут к тому, что все LinkDemands, удовлетворяющие требованиям, будут преобразованы в полные требования во время выполнения, что может вызвать проблемы с производительностью. В сборках набора правил безопасности для сборок уровня 2 прозрачные методы не будут компилироваться в JIT-компиляторе, если они пытаются удовлетворить требования LinkDemand.

В сборках, использующих безопасность уровня 2, попытки метода, прозрачного для безопасности, отвечают требованиям LinkDemand или вызывают метод в сборке, не <xref:System.MethodAccessException>являющейся сборкой APTCA, вызывают a; в сборках уровня 1 требование LinkDemand станет полным требованием.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, пометьте метод <xref:System.Security.SecurityCriticalAttribute> доступа атрибутом или <xref:System.Security.SecuritySafeCriticalAttribute> или удалите LinkDemand из метода доступа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В этом примере прозрачный метод пытается вызвать метод, имеющий LinkDemand. Это правило будет срабатывать в этом коде.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]