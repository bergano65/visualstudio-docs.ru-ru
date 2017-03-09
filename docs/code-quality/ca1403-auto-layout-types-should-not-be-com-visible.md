---
title: "CA1403: типы макета Auto не должны быть видимыми для COM | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: типы макета Auto не должны быть видимыми для COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый для COM тип значения помечен атрибутом <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> со значением <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## Описание правила  
 Типы макета <xref:System.Runtime.InteropServices.LayoutKind> управляются средой CLR.  Макеты этих типов могут меняться в различных версиях платформы .NET Framework, что может привести к нарушению работы клиентов COM, которые ожидают определенного макета.  Обратите внимание, что, если атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute> не указан, компиляторы C\#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] и C\+\+ указывают для типов значения макет <xref:System.Runtime.InteropServices.LayoutKind>.  
  
 Если не указано иное, все открытые и не универсальные типы являются видимыми для COM; все не открытые и универсальные типы являются невидимыми для COM.  Однако чтобы снизить количество ложных положительных результатов, данное правило требует явно указывать видимость типа для COM; содержащая тип сборка должна быть помечена атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>, для которого установлено значение `false`, а тип необходимо пометить атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> со значением `true`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, установите для атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute> значение <xref:System.Runtime.InteropServices.LayoutKind> или <xref:System.Runtime.InteropServices.LayoutKind>. Можно также сделать тип невидимым для COM.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило, и тип, удовлетворяющий ему.  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## Связанные правила  
 [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## См. также  
 [Introducing the Class Interface](http://msdn.microsoft.com/ru-ru/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)