---
title: "CA2145: прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный метод, метод, помеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>, или тип, который содержит метод, помеченный атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Описание правила  
 Методы, оснащенные атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>, имеют неявную проверку LinkDemand, помещаемую после вызова ее любым методом.  Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности.  Пометка метода, который использует SuppressUnmanagedCodeSecurity с атрибутом <xref:System.Security.SecurityCriticalAttribute>, делает это требование более очевидным для тех, кто вызывает этот метод.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, следует отметить метод или тип атрибутом <xref:System.Security.SecurityCriticalAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
### Код  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Комментарии