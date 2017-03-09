---
title: "CA2107: проверьте использование deny и permit only | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: проверьте использование deny и permit only
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод содержит проверку безопасности, которая задает действие безопасности PermitOnly или Deny.  
  
## Описание правила  
 Действия безопасности [Using the PermitOnly Method](http://msdn.microsoft.com/ru-ru/8c7bdb7f-882f-45b7-908c-6cbaa1767649) и <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> могут использовать только пользователи, обладающие достаточными знаниями о безопасности [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Код, который использует эти действия безопасности, должен быть тщательно проанализирован на предмет безопасности.  
  
 Действие безопасности Deny изменяет поведение прохода стека, заданное по умолчанию, которое возникает в ответ на запрос безопасности.  Оно позволяет указать разрешения, которые не должны предоставляться в течение метода отказа, независимо от фактических разрешений вызывающих методов в стеке вызова.  Если при проходе стека обнаруживается метод, защищенный действием Deny, и если запрашиваемое разрешение входит в число отклоненных разрешений, происходит сбой прохода стека.  Действие безопасности PermitOnly изменяет поведение прохода стека, заданное по умолчанию.  Оно позволяет коду указывать только те разрешения, которые могут быть предоставлены независимо от разрешений вызывающих методов.  Если при проходе стека обнаруживается метод, защищенный действием PermitOnly, и если запрашиваемое разрешение не входит в число разрешений, указанных действием PermitOnly, происходит сбой прохода стека.  
  
 Код, в основе которого лежат эти действия, необходимо тщательно анализировать на предмет уязвимостей безопасности, что обусловлено ограниченной пригодностью и неявным поведением этих действий.  Рассмотрим следующий пример.  
  
-   Действия Deny или PermitOnly не влияют на [Link Demands](../Topic/Link%20Demands.md).  
  
-   Если Deny или PermitOnly происходят в одном и том же фрейме стека, что и запрос, вызывающий проход стека, действия безопасности никак не отражаются.  
  
-   Значения, используемые для формирования основанных на путях разрешений, обычно можно указать несколькими способами.  Запрет доступа к одной форме пути не запрещает доступ ко всем формам.  Например, если общий ресурс \\\\Server\\Share назначен на сетевой диск X:, то для запрета доступа к файлу в общей папке необходимо запретить \\\\Server\\Share\\File, X:\\File и все остальные пути, обращающиеся к файлу.  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> может остановить проход стека, прежде чем будут достигнуты Deny или PermitOnly.  
  
-   Если Deny не дает результатов, а именно, когда вызывающий метод имеет разрешение, заблокированное действием Deny, то вызывающий метод может обращаться к защищенному ресурсу напрямую, минуя Deny.  Подобным образом, если вызывающий метод не имеет отклоненного разрешения, произойдет сбой прохода стека без Deny.  
  
## Устранение нарушений  
 Любое использование этих действий безопасности вызовет нарушение.  Устранить нарушение можно, если не использовать эти действия безопасности.  
  
## Отключение предупреждений  
 Отключать предупреждение из этого правила рекомендуется только после анализа безопасности.  
  
## Пример  
 В следующем примере показаны некоторые ограничения действия Deny.  
  
 В следующей библиотеке содержится класс с двумя одинаковыми методами; они отличаются только запросами безопасности, защищающими их.  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## Пример  
 В следующем приложении демонстрируется действие Deny с защищенными методами из библиотеки.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **Demand: запрет вызывающего объекта не оказывает влияния на запрос с утверждаемым разрешением.**  
**LinkDemand: запрет вызывающего объекта не оказывает влияния на LinkDemand с утверждаемым разрешением.**  
**LinkDemand: этот запрет не оказывает влияния на код, защищенный LinkDemand.**  
**LinkDemand: этот запрет не оказывает влияния на код, защищенный LinkDemand.**   
## См. также  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/ru-ru/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/ru-ru/8c7bdb7f-882f-45b7-908c-6cbaa1767649)