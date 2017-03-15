---
title: "CA2138: прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный метод безопасности вызывает метод, помеченный атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Описание правила  
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью P\/Invoke \(неуправляемого\) вызова.  Методы P\/Invoke и COM\-взаимодействия, которые помечены с помощью атрибута <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>, приводят к выполнению LinkDemand относительно вызывающего метода.  Поскольку прозрачный код безопасности не может удовлетворить требования LinkDemand, код также не может вызывать методы, помеченные атрибутом SuppressUnmanagedCodeSecurity, или методы класса, помеченного атрибутом SuppressUnmanagedCodeSecurity.  Метод выдаст ошибку, или требования будут преобразованы в полные требования.  
  
 Нарушения этого правила могут вызвать исключение <xref:System.MethodAccessException> на модели прозрачности безопасности 2 уровня и применение полных требований для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> в модели прозрачности 1 уровня.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> и отметьте метод атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]