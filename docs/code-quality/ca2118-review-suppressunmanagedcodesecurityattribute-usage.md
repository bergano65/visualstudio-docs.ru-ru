---
title: "CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный тип или член имеет атрибут <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>.  
  
## Описание правила  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> изменяет поведение системы безопасности, определенное по умолчанию, для членов, выполняющих неуправляемый код за счет COM\-взаимодействия или вызова платформы.  Как правило, система открывает [Данные и модели](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) для разрешения неуправляемого кода.  Эта необходимость возникает во время выполнения для каждого вызова члена и проверяется разрешение каждого вызывающего метода в стеке вызова.  Когда атрибут присутствует, система создает [Link Demands](../Topic/Link%20Demands.md) для разрешения: разрешения непосредственно вызывающего метода проверяются во время JIT\-компиляции вызывающего метода.  
  
 Этот атрибут служит в основном для повышения производительности; однако, прирост производительности сопряжен со значительными рисками безопасности.  Если атрибут поместить в открытые члены, вызывающие встроенные методы, вызывающему методу в стеке вызова \(только не непосредственно вызывающему методу\) не потребуется разрешение на неуправляемый код для его выполнения.  В зависимости от действий открытого члена и обработки ввода ненадежным вызывающим методам может предоставляться доступ к функциональным возможностям, которые, как правило, недоступны надежному коду.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] основывается на проверках безопасности для предотвращения получения прямого доступа вызывающих методов к текущему адресному пространству процесса.  Поскольку данный атрибут обходит обычную безопасность, код может представлять серьезную угрозу, если с его помощью можно выполнять операции чтения или записи в память процесса.  Следует отметить, что риск не ограничивается только методами, которые преднамеренно предоставляют доступ к памяти процесса; они могут возникать в любой ситуации, когда злонамеренному коду удается получить доступ любыми способами, например, путем подстановки непредвиденных, искаженных или недопустимых входных данных.  
  
 Согласно политике безопасности по умолчанию, разрешение неуправляемого кода на сборку не предоставляется, если он не выполняется с локального компьютера или не является членом одной из следующих групп:  
  
-   Группа кода "My Computer Zone"  
  
-   Группа кода "Microsoft Strong Name"  
  
-   Группа кода "ECMA Strong Name"  
  
## Устранение нарушений  
 Тщательно проанализируйте свой код и убедитесь, что этот атрибут абсолютно необходим.  Если вы не знакомы с задачами обеспечения безопасности неуправляемого кода или вам не известны результаты, к которым может привести использование этого атрибута, удалите его из своего кода.  Если атрибут является обязательным, необходимо обеспечить, чтобы вызывающие методы не смогли использовать код злонамеренно.  Если код не имеет разрешения на выполнение неуправляемого кода, этот атрибут может не действовать и его следует удалить.  
  
## Отключение предупреждений  
 Чтобы отключить предупреждение из этого правила без последствий, необходимо обеспечить, чтобы вызывающие методы не предоставляли доступ к встроенным операциям или ресурсам, которые могут использоваться деструктивно.  
  
## Пример  
 В следующем примере нарушается это правило.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Пример  
 В следующем примере метод `DoWork` предоставляет открытый путь кода к методу вызова платформы `FormatHardDisk`.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Пример  
 В следующем примере открытый метод `DoDangerousThing` вызывает нарушение.  Чтобы устранить это нарушение, `DoDangerousThing` должен быть закрытым и доступ к нему должен предоставляться через открытый метод, защищенный запросом безопасности, как показано в методе `DoWork`.  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## См. также  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/ru-ru/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Данные и модели](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Link Demands](../Topic/Link%20Demands.md)