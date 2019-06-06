---
title: CA2107. Проверьте использование Deny и Permit Only
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7f3bdc6351f30d5cad60a7ed9663824fa3d434
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714711"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107. Проверьте использование Deny и Permit Only

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Метод содержит проверку безопасности, которая задает действие безопасности PermitOnly или Deny.

## <a name="rule-description"></a>Описание правила

<xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Действие по обеспечению безопасности должен использоваться только те, кто имеет специальными знаниями в области безопасности .NET. Код, который использует эти действия безопасности, должен быть тщательно проанализирован на предмет безопасности.

Запретить изменяет поведение по умолчанию стека, которая происходит в ответ на требование безопасности. Он позволяет задать разрешения, которые не должны предоставляться в течение метода отказа, независимо от того, фактические разрешения вызывающих методов в стеке вызовов. Если обход стека обнаруживается метод, который будет защищен Deny, и если затребованное разрешение включается в запрещенные разрешения, обход стека не выполняется. PermitOnly также изменяет поведение по умолчанию стека. Оно позволяет коду указывать только те разрешения, которые могут предоставляться независимо от разрешений от вызывающих объектов. Если обход стека определяет метод, который будет защищен PermitOnly и если затребованное разрешение не включается в разрешения, которые определяются PermitOnly, обход стека не выполняется.

Код, основанный на эти действия, необходимо тщательно оценить уязвимостей в системе безопасности из-за ограниченной пригодностью и поведении. Рассмотрим следующий пример.

- [Требования связывания](/dotnet/framework/misc/link-demands) не затрагивает Deny или PermitOnly.

- Если Deny или PermitOnly происходит в том же кадре стека, как запрос, вызывающий стека, действия безопасности не оказывают влияния.

- Значения, используемые для создания разрешения на основе пути обычно можно указать несколькими способами. Запрет на доступ к одной форме пути не запрещает доступ для всех форм. Например, если в общую \\\Server\Share сопоставляется с сетевой диск X:, чтобы запретить доступ к файлу в общей папке, необходимо запретить \\\Server\Share\File X:\File и каждого пути, который обращается к файлу.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Может завершить стека, прежде чем будет достигнут Deny или PermitOnly.

- Если Deny не дает результатов, а именно, когда вызывающий объект имеет разрешение, которое блокирует Deny, вызывающий объект можно получить доступ к защищенному ресурсу напрямую, минуя Deny. Аналогичным образом Если вызывающий объект не имеет запрещенным разрешением, обход стека завершится сбоем без Deny.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Любое использование этих действий безопасности будет вызывать нарушение. Чтобы устранить нарушение, не используйте эти действия по обеспечению безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, только в том случае, после завершения проверки безопасности.

## <a name="example-1"></a>Пример 1

В следующем примере показано некоторые ограничения действия Deny. Библиотека содержит класс, имеющий два метода, которые идентичны, за исключением требований безопасности, которые защищают транзакции.

[!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Пример 2

В следующем приложении демонстрируется действие Deny с защищенными методами из библиотеки.

[!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

В этом примере выводятся следующие данные:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>См. также

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)