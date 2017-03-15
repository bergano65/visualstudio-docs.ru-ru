---
title: "CA1413: избегайте использования не открытых полей в видимых типах значений COM | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: избегайте использования не открытых полей в видимых типах значений COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип значения, специально помеченный как отображаемый для COM, объявляет закрытое поле экземпляра.  
  
## Описание правила  
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM\-клиентов.  Проверьте содержимое полей на наличие сведений, к которым не должен предоставляться доступ или которые могут оказать непреднамеренное воздействие на разработку или безопасность.  
  
 По умолчанию все открытые типы значений отображаются для COM.  Тем не менее чтобы уменьшить число ложных положительных результатов, это правило требует видимость COM для типа, который будет явно указан.  Содержащая сборка должна быть помечена атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> со значением `false`, и тип должен быть помечен с помощью атрибута <xref:System.Runtime.InteropServices.ComVisibleAttribute> равного `true`.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила и оставить поле скрытым, измените тип значения на ссылочный или удалите атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> из типа.  
  
## Отключение предупреждений  
 Если использование открытого поля допустимо, можно отключить вывод предупреждений для данного правила.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Связанные правила  
 [CA1407: не используйте статические члены в видимых COM типах](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## См. также  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)