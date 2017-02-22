---
title: "CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачному методу необходимо требование <xref:System.Security.Permissions.SecurityAction> или другое требование безопасности.  
  
## Описание правила  
 Это правило срабатывает для прозрачных методов, для доступа к которым требуется LinkDemand.  Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений.  Поскольку предполагается, что прозрачные методы являются нейтральными в плане безопасности, они не должны принимать какие\-либо решения по безопасности.  Кроме того, критичный в плане безопасности код, который принимает решения по безопасности, не должен полагаться на прозрачный код, который ранее принимал такое решение.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, удалите требование компоновки прозрачного метода или отметьте метод атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>, если он выполняет проверки безопасности, такие как проверка требований безопасности.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере это правило срабатывает в методе, поскольку метод является прозрачным и помечается LinkDemand <xref:System.Security.PermissionSet>, который содержит <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Для этого правила отключать вывод предупреждений не следует.