---
title: CA2143. Прозрачные методы не должны использовать требования безопасности
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231987"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143. Прозрачные методы не должны использовать требования безопасности

|||
|-|-|
|TypeName|транспарентмесодсшаулднотдеманд|
|CheckId|CA2143|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Тип или метод транпарент декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` требованием, <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> или метод вызывает метод.

## <a name="rule-description"></a>Описание правила
Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Любой код, выполняющий проверки безопасности, такие как требования безопасности, должен быть критически важным для защиты.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Как правило, чтобы устранить нарушение этого правила, пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом. Это требование также можно удалить.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
Файлы правил в следующем коде, поскольку прозрачный метод делает декларативное требование к безопасности.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>См. также
[CA2142: Прозрачный код не должен быть защищен с помощью LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)