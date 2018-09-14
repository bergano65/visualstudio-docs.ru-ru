---
title: 'CA2133: делегаты должны привязываться к методам с согласованной прозрачностью'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11f6738d1f280869d5390b8109e61a6efb9c64b9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545545"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: делегаты должны привязываться к методам с согласованной прозрачностью

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия среды CLR, предназначенную для веб-приложения Silverlight).

## <a name="cause"></a>Причина

Это предупреждение вызывается методом, который привязывает делегат, помеченный с <xref:System.Security.SecurityCriticalAttribute> в метод, который является прозрачным или помечен с помощью <xref:System.Security.SecuritySafeCriticalAttribute>. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.

## <a name="rule-description"></a>Описание правила

Типы делегатов и методы, которые они привязаны к должны иметь согласованную прозрачность. Прозрачные и надежными с точки зрения делегаты только может привязываться к другой прозрачный или безопасный методы. Аналогичным образом критические делегатов может только привязать критические методы. Эти правила привязки убедитесь, что единственным кодом, который можно вызвать метод через делегат также может вызвать тот же метод напрямую. Например правила привязки запретить прозрачный код вызова кода critical непосредственно через прозрачный делегат.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, который привязывает таким образом, чтобы прозрачность двух эквивалентны.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]