---
title: CA2133. Делегаты должны быть привязаны к методам с соответствующей прозрачностью
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14061c0f54593a2cb9b591d39cb46a433b0e34be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232311"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133. Делегаты должны быть привязаны к методам с соответствующей прозрачностью

|||
|-|-|
|TypeName|делегатесмустбиндвисконсистенттранспаренци|
|CheckId|CA2133|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
> Это предупреждение применяется только к коду, на котором работает CoreCLR (версия CLR, относящаяся к веб-приложениям Silverlight).

## <a name="cause"></a>Причина:

Это предупреждение срабатывает для метода, который привязывает делегат, помеченный <xref:System.Security.SecurityCriticalAttribute> как, к методу, который является прозрачным или помеченным <xref:System.Security.SecuritySafeCriticalAttribute>атрибутом. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.

## <a name="rule-description"></a>Описание правила

Типы делегатов и методы, к которым они привязаны, должны иметь одинаковую прозрачность. Прозрачные и критические для безопасности делегаты могут быть привязаны только к другим прозрачным или безопасным методам. Аналогичным образом, критические делегаты могут быть привязаны только к критическим методам. Эти правила привязки гарантируют, что единственный код, который может вызвать метод через делегат, может также вызывать тот же метод напрямую. Например, правила привязки не позволяют прозрачному коду вызывать критический код непосредственно через прозрачный делегат.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, к которому он привязан, чтобы прозрачность этих двух эквивалентна.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]