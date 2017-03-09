---
title: "CA1412: помечайте интерфейсы ComSource как IDispatch | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: помечайте интерфейсы ComSource как IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип помечен атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> и как минимум один из указанных интерфейсов не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> со значением `InterfaceIsDispatch`.  
  
## Описание правила  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> используется для идентификации интерфейсов событий, предоставляемых классом для клиентов COM.  Чтобы клиенты COM Visual Basic 6 могли получать уведомления о событиях, эти интерфейсы должны быть представлены в виде `InterfaceIsIDispatch`.  По умолчанию интерфейс, не помеченный с помощью атрибута <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, выводится как двойной интерфейс.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте или измените атрибут <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> так, чтобы в качестве его значения было задано InterfaceIsIDispatch для всех интерфейсов, заданных с атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан класс, в котором один из интерфейсов нарушает правило.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Связанные правила  
 [CA1408: не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## См. также  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/ru-ru/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)