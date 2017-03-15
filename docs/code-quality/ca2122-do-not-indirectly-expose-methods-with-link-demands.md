---
title: "CA2122: не используйте косвенное представление методов с запросами компоновки | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: не используйте косвенное представление методов с запросами компоновки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый или защищенный член имеет [Link Demands](../Topic/Link%20Demands.md) и вызывается членом, который не выполняет каких\-либо проверок безопасности.  
  
## Описание правила  
 Запрос компоновки проверяет разрешения только непосредственно вызывающего метода.  Если член `X` не предъявляет требований к безопасности своих вызывающих методов и вызывает код, защищенный запросом компоновки, вызывающий метод без необходимого разрешения может использовать `X` для доступа к защищенному члену.  
  
## Устранение нарушений  
 Добавьте безопасный [Данные и модели](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) или запрос компоновки к члену, так чтобы он более не предоставлял небезопасный доступ к члену, защищенному запросом компоновки.  
  
## Отключение предупреждений  
 Чтобы отключить предупреждения из этого правила без последствий, необходимо удостовериться, чтобы код не предоставлял доступ к операциям или ресурсам, которые можно использовать небезопасным образом.  
  
## Пример  
 В следующих примерах показана библиотека, нарушающая правило, а также приложение, демонстрирующее слабость библиотеки.  Пример библиотеки содержит два метода, которые вместе нарушают правило.  Метод `EnvironmentSetting` защищен запросом компоновки для предоставления сборкам неограниченного доступа ко всем переменным среды.  Метод `DomainInformation` не предъявляет требований к безопасности своих вызывающих методов, так как он вызывает `EnvironmentSetting`.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Пример  
 Следующее приложение вызывает незащищенный член библиотеки.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **Значение из незащищенного члена: seattle.corp.contoso.com**   
## См. также  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Данные и модели](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)