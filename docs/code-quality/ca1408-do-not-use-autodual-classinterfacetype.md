---
title: "CA1408: не используйте AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: не используйте AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый для COM тип значения помечен атрибутом <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>, у которого для `AutoDual` установлено значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## Описание правила  
 Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса.  Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM\-клиентов, связанных с интерфейсом.  По умолчанию, если атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> не указан, используется только диспетчерский интерфейс.  
  
 Если не указано иное, все открытые и не универсальные типы являются видимыми для COM; все не открытые и универсальные типы являются невидимыми для COM.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, измените значение атрибута <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> на `None` типа <xref:System.Runtime.InteropServices.ClassInterfaceType> и явным образом определите интерфейс.  
  
## Отключение предупреждений  
 Не отключайте предупреждения этого правила, если вы не уверены, что макет типа и его базовые типы останутся неизменными в последующей версии.  
  
## Пример  
 В следующем примере показан класс, нарушающий это правило, и повторное объявление класса с использованием явного интерфейса.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Связанные правила  
 [CA1403: типы макета Auto не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## См. также  
 [Introducing the Class Interface](http://msdn.microsoft.com/ru-ru/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)