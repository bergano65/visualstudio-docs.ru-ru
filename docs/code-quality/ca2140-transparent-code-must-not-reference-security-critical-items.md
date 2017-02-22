---
title: "CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности | Microsoft Docs"
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
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный метод:  
  
-   обрабатывает критичный в плане безопасности тип исключения безопасности  
  
-   имеет параметр, который помечен как тип, критичный в плане безопасности  
  
-   имеет универсальный параметр с ограничениями, критичными в плане безопасности  
  
-   имеет локальную переменную типа, критичного в плане безопасности  
  
-   ссылается на тип, помеченный как критичный в плане безопасности  
  
-   вызывает метод, помеченный как критичный в плане безопасности  
  
-   ссылается на поле, помеченное как критичное в плане безопасности  
  
-   возвращает тип, помеченный как критичный в плане безопасности  
  
## Описание правила  
 Элемент кода, помеченный атрибутом <xref:System.Security.SecurityCriticalAttribute>, является критичным в плане безопасности.  Прозрачный метод не может использовать элемент, критический с точки зрения безопасности.  Если прозрачный тип пытается использовать тип, критичный в плане безопасности, то вызывается исключение <xref:System.TypeAccessException>, <xref:System.MethodAccessException> или <xref:System.FieldAccessException>.  
  
## Устранение нарушений  
 Чтобы устранить это нарушение, выполните одно из следующих действий.  
  
-   Пометьте элемент кода, использующий критичный в плане безопасности код с атрибутом <xref:System.Security.SecurityCriticalAttribute>  
  
     \- либо \-  
  
-   Удалите атрибут <xref:System.Security.SecurityCriticalAttribute> из элементов кода, помеченных как критичные в плане безопасности, и измените их метку, воспользовавшись атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityTransparentAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующих примерах прозрачный метод пытается обратиться к критичной в плане безопасности универсальной коллекции, а также к критичным в плане безопасности полю и методу.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## См. также  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>