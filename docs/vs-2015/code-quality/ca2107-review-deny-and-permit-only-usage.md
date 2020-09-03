---
title: 'CA2107: проверка только запретов и разрешений на использование | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547775"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107. Проверьте использование Deny и Permit Only
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод содержит проверку безопасности, которая указывает действие безопасности PermitOnly или Deny.

## <a name="rule-description"></a>Описание правила
 [С помощью метода PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) и <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> действий безопасности следует использовать только те, кто обладает расширенными знаниями о [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] безопасности. Код, который использует эти действия безопасности, должен быть тщательно проанализирован на предмет безопасности.

 Deny изменяет поведение по умолчанию для прохода стека, которое происходит в ответ на требование безопасности. Он позволяет указать разрешения, которые не должны быть предоставлены в течение метода Deny, независимо от фактических разрешений вызывающих объектов в стеке вызовов. Если проверка стека обнаруживает метод, защищенный Deny, и если требуемое разрешение включено в запрещенные разрешения, то проверка стека завершается ошибкой. PermitOnly также изменяет поведение по умолчанию для прохода стека. Он позволяет коду указывать только те разрешения, которые могут быть предоставлены, независимо от разрешений вызывающих объектов. Если проверка стека обнаруживает метод, защищенный с помощью PermitOnly, и если требуемое разрешение не включено в разрешения, заданные с помощью PermitOnly, то проверка стека завершается ошибкой.

 Код, основанный на этих действиях, следует тщательно оценить на наличие уязвимостей в системе безопасности из-за их ограниченной полезности и незаметного поведения. Рассмотрим следующий пример.

- На [запросы ссылок](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) не влияет Deny или PermitOnly.

- Если Deny или PermitOnly происходит в том же кадре стека, что и требование, вызывающее проверку стека, действия безопасности не действуют.

- Значения, используемые для создания разрешений на основе пути, обычно можно указать несколькими способами. Запрет доступа к одной форме пути не запрещает доступ ко всем формам. Например, если общая папка \\ \сервер\шаре сопоставлена с сетевым диском X:, чтобы запретить доступ к файлу в общей папке, необходимо запретить \\ \Сервер\шаре\филе, КС:\филе и все остальные пути, обращающиеся к файлу.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>Может завершить проверку стека до достижения Deny или PermitOnly.

- Если оператор DENY имеет любой результат, а именно, если у вызывающего объекта есть разрешение, заблокированное Deny, вызывающий объект может напрямую получить доступ к защищенному ресурсу, минуя Deny. Аналогично, если вызывающий объект не имеет запрещенного разрешения, проверка стека завершится ошибкой без Deny.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Любое использование этих действий безопасности приведет к нарушению. Чтобы устранить нарушение, не используйте эти действия безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила только после завершения проверки безопасности.

## <a name="example"></a>Пример
 В следующем примере показаны некоторые ограничения Deny.

 Следующая библиотека содержит класс с двумя методами, идентичными, за исключением требований безопасности, защищающих их.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении показано влияние DENY на защищенные методы из библиотеки.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 В этом примере формируются следующие данные:

 **Demand: Deny вызывающего объекта не оказывает влияния на запрос с утвержденным разрешением.** 
 **LinkDemand: Deny вызывающего объекта не влияет на LinkDemand с утвержденным разрешением.** 
 **LinkDemand: Deny вызывающего объекта не влияет на код, защищенный с помощью LinkDemand.** 
 **LinkDemand: этот запрет не влияет на код, защищенный с помощью LinkDemand.**
## <a name="see-also"></a>См. также
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Рекомендации по безопасному кодированию](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) , [переопределяющие проверки безопасности](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [с помощью метода PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
