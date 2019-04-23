---
title: CA2107. Просмотрите deny и permit only | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7de14898c5fb2bb6f8e95a2af5fd6b39a54cdb1d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082156"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107. Проверьте использование Deny и Permit Only
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод содержит проверку безопасности, которая задает действие безопасности PermitOnly или Deny.

## <a name="rule-description"></a>Описание правила
 [Использование метода PermitOnly](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) и <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> действия по обеспечению безопасности должен использоваться только те, кто имеет специальными знаниями в области из [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] безопасности. Код, который использует эти действия безопасности, должен быть тщательно проанализирован на предмет безопасности.

 Запретить изменяет поведение по умолчанию стека, которая происходит в ответ на требование безопасности. Он позволяет задать разрешения, которые не должны предоставляться в течение метода отказа, независимо от того, фактические разрешения вызывающих методов в стеке вызовов. Если обход стека обнаруживается метод, который будет защищен Deny, и если затребованное разрешение включается в запрещенные разрешения, обход стека не выполняется. PermitOnly также изменяет поведение по умолчанию стека. Оно позволяет коду указывать только те разрешения, которые могут предоставляться независимо от разрешений от вызывающих объектов. Если обход стека определяет метод, который будет защищен PermitOnly и если затребованное разрешение не включается в разрешения, которые определяются PermitOnly, обход стека не выполняется.

 Код, основанный на эти действия, необходимо тщательно оценить уязвимостей в системе безопасности из-за ограниченной пригодностью и поведении. Рассмотрим следующий пример.

- [Требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) не затрагивает Deny или PermitOnly.

- Если Deny или PermitOnly происходит в том же кадре стека, как запрос, вызывающий стека, действия безопасности не оказывают влияния.

- Значения, используемые для создания разрешения на основе пути обычно можно указать несколькими способами. Запрет на доступ к одной форме пути не запрещает доступ для всех форм. Например, если в общую \\\Server\Share сопоставляется с сетевой диск X:, чтобы запретить доступ к файлу в общей папке, необходимо запретить \\\Server\Share\File, X:\File и каждого пути, который обращается к файлу.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Может завершить стека, прежде чем будет достигнут Deny или PermitOnly.

- Если Deny не дает результатов, а именно, когда вызывающий объект имеет разрешение, которое блокирует Deny, вызывающий объект можно получить доступ к защищенному ресурсу напрямую, минуя Deny. Аналогичным образом Если вызывающий объект не имеет запрещенным разрешением, обход стека завершится сбоем без Deny.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Любое использование этих действий безопасности будет вызывать нарушение. Чтобы устранить нарушение, не используйте эти действия по обеспечению безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, только в том случае, после завершения проверки безопасности.

## <a name="example"></a>Пример
 В следующем примере показано некоторые ограничения действия Deny.

 Следующая библиотека содержит класс, имеющий два метода, которые идентичны, за исключением требований безопасности, которые защищают транзакции.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении демонстрируется действие Deny с защищенными методами из библиотеки.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 В этом примере формируются следующие данные:

 **Запросу: Запретить вызывающей стороны не оказывает влияния по запросу с помощью утвержденного разрешения. ** 
 **LinkDemand: Запретить вызывающей стороны не влияет на LinkDemand с утвержденного разрешения. ** 
 **LinkDemand: Запретить вызывающей стороны не оказывает влияния с помощью кода, защищенного с помощью LinkDemand. ** 
 **LinkDemand: Этот запрет не оказывает влияния с помощью кода, защищенного с помощью LinkDemand.**
## <a name="see-also"></a>См. также
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [переопределения проверок безопасности](http://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [использование метода PermitOnly](http://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
