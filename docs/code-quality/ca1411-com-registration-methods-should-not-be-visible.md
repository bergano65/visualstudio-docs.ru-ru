---
title: "CA1411: методы регистрации для COM-клиента не должны быть видимыми | Microsoft Docs"
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
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411: методы регистрации для COM-клиента не должны быть видимыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод, помеченный атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> доступен для внешнего кода.  
  
## Описание правила  
 При регистрации сборки для модели COM в реестр добавляются записи для каждого типа сборки, доступного для COM.  Методы, помеченные атрибутами <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> и <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>, вызываются в процессе регистрации и отмены регистрации соответственно для запуска пользовательского кода, относящегося к регистрации и отмене регистрации данных типов.  Этот код не должен вызываться за пределами этих процессов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените доступность данного метода на `private` или `internal` \(`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показаны два метода, которые нарушают данное правило.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## Связанные правила  
 [CA1410: методы регистрации для COM\-клиента должны быть соответствующими](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## См. также  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)