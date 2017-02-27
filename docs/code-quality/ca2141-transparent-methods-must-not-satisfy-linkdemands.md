---
title: "CA2141: прозрачные методы не должны удовлетворять требования LinkDemand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2141: прозрачные методы не должны удовлетворять требования LinkDemand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный метод безопасности вызывает метод в сборке, не помеченный атрибутом <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\), или прозрачный метод безопасности удовлетворяет требование <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` для типа или метода.  
  
## Описание правила  
 Требованиям LinkDemand соответствует критически важная для безопасности операция, которая может вызвать несанкционированное повышение привилегий.  Прозрачный для системы безопасности код не должен удовлетворять требованиям LinkDemand, поскольку его не затрагивают те же требования аудита безопасности, как код, критичный в плане безопасности.  Прозрачные методы в сборках набора правил безопасности уровня 1 приводят к тому, что все требования LinkDemands, которым они удовлетворяют, преобразуются в полные требования во время выполнения, что может вызвать проблемы с производительностью.  В сборках с набором правил безопасности уровня 2 компиляция прозрачных методов в JIT\-компиляторе завершится неудачно, если они будут пытаться удовлетворить требование LinkDemand.  
  
 В сборках, использующих уровень безопасности 2, попытки прозрачного метода безопасности удовлетворить требование LinkDemand или вызвать метод в сборке, не являющейся сборкой APTCA, вызывают исключение <xref:System.MethodAccessException>; в сборках с уровнем безопасности 1 требование LinkDemand становится полным требованием.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, отметьте метод доступа атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> или удалите LinkDemand из метода доступа.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В этом примере прозрачный метод пытается вызвать метод, который имеет требование LinkDemand.  Это правило срабатывает на этот код.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]