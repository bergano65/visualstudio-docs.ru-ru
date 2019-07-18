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
ms.openlocfilehash: 17160e5fd47491dddb22a28d4b3f7464ad3efb78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806793"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143. Прозрачные методы не должны использовать требования безопасности

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Tranparent тип или метод декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` запросу или вызовы методов <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> метод.

## <a name="rule-description"></a>Описание правила
 Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Вместо этого следует надежными с точки зрения любой код, который выполняет проверки безопасности, такие как требования безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Как правило, чтобы устранить нарушение этого правила, пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибута. Можно также удалить требование.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Правило файлы на следующий код, поскольку прозрачный метод создает требование декларативной безопасности.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>См. также
 [CA2142: Прозрачный код не должен быть защищен с помощью требований LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)