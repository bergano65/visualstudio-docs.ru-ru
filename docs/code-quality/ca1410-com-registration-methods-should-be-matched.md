---
title: "CA1410: методы регистрации для COM-клиента должны быть соответствующими | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: методы регистрации для COM-клиента должны быть соответствующими
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## Причина  
 В типе объявляется метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>, но не объявляется метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, или наоборот.  
  
## Описание правила  
 Для создания COM\-клиентами типа [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] необходимо сначала зарегистрировать этот тип.  Если это возможно, в процессе регистрации вызывается метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, для выполнения определенного пользователем кода.  В процессе отмены регистрации вызывается метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, чтобы обратить операции метода регистрации.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте соответствующий метод регистрации или отмены регистрации.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  В помеченном метками комментария коде показано исправления этого нарушения.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Связанные правила  
 [CA1411: методы регистрации для COM\-клиента не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## См. также  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)