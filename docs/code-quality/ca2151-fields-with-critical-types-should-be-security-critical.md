---
title: "CA2151. Поля с критическими типами должны быть критическими с точки зрения безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA2151. Поля с критическими типами должны быть критическими с точки зрения безопасности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## Причина  
 Объявлено прозрачное для безопасности поле или поле, надежное с точки зрения безопасности.  Его тип определяется как критический с точки зрения безопасности.  Например:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 В этом примере `m_field` — это прозрачное для безопасности поле критического с точки зрения безопасности типа.  
  
## Описание правила  
 Для использования критических с точки зрения безопасности типов код, который ссылается на тип, должен быть либо критическим с точки зрения безопасности, либо надежным с точки зрения безопасности.  Это верно даже в случае косвенной ссылки.  Например, при ссылке на прозрачное поле критического для безопасности типа код должен быть либо критическим с точки зрения безопасности, либо надежным с точки зрения безопасности.  Поэтому применять прозрачное для безопасности поле или поле, надежное с точки зрения безопасности, не рекомендуется, поскольку прозрачный код по\-прежнему не сможет получить доступ к полю.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, отметьте поле атрибутом <xref:System.Security.SecurityCriticalAttribute> или сделайте тип, на который ссылается поле, прозрачным с точки зрения безопасности либо надежным с точки зрения безопасности.  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
### Код  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### Комментарии