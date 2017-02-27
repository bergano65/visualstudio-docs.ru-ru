---
title: "CA2149: прозрачные методы не следует вызывать в машинном коде | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2149: прозрачные методы не следует вызывать в машинном коде
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод вызывает собственную функцию через прототип метода, например P\/Invoke.  
  
## Описание правила  
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью вызова P\/Invoke.  Нарушения этого правила могут вызвать исключение <xref:System.MethodAccessException> на модели прозрачности 2 уровня и применение полных требований для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> в модели прозрачности 1 уровня.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, отметьте метод, вызывающий машинный код, атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]