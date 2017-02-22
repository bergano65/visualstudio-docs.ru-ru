---
title: "CA2111: указатели не должны быть видимыми | Microsoft Docs"
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
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2111: указатели не должны быть видимыми
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытое или защищенное поле <xref:System.IntPtr?displayProperty=fullName> или <xref:System.UIntPtr?displayProperty=fullName> доступно не только для чтения.  
  
## Описание правила  
 Поля <xref:System.IntPtr> и <xref:System.UIntPtr> принадлежат к типам указателей, используемых для доступа к неуправляемой памяти.  Если указатель не является закрытым, внутренним или доступным только для чтения, злоумышленный код может изменить его значение, что может позволить получить доступ к произвольным областям памяти или вызвать сбой приложения или системы.  
  
 Сведения об обеспечении безопасного доступа к типу, содержащему поле указателя, см. в разделе [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Устранение нарушений  
 Обеспечьте безопасность указателя, сделав его доступным только для чтения, внутренним или закрытым.  
  
## Отключение предупреждений  
 Предупреждения о нарушении этого правила можно отключить, если значение указателя не имеет большого значения.  
  
## Пример  
 В следующем примере показаны два указателя, один из которых нарушает данное правило, а другой удовлетворяет ему.  Обратите внимание, что указатели, которые не являются закрытыми, также нарушают правило [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Связанные правила  
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## См. также  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>