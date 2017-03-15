---
title: "Атрибут System.ObsoleteAttribute нельзя применять к определениям AddHandler, RemoveHandler и RaiseEvent | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут System.ObsoleteAttribute нельзя применять к определениям AddHandler, RemoveHandler и RaiseEvent
Атрибут System.ObsoleteAttribute нельзя применять к определениям AddHandler, RemoveHandler и RaiseEvent. При необходимости примените этот атрибут непосредственно к событию.  
  
 Настраиваемое событие применяет <xref:System.ObsoleteAttribute> к своей процедуре `AddHandler`, `RemoveHandler` или `RaiseEvent`.  
  
 Атрибут <xref:System.ObsoleteAttribute> помечает программный элемент как больше не используемый и уведомляет пользователей, что этот элемент должен быть удален в будущих версиях продукта.  
  
 Не имеет смысла продолжать использовать некоторые части настраиваемого события, когда другие части больше не используются.  
  
 **Идентификатор ошибки:** BC31142  
  
### Исправление ошибки  
  
-   Удалите <xref:System.ObsoleteAttribute> из объявления отдельной процедуры и примените его к всему объявлению события.  
  
## См. также  
 <xref:System.ObsoleteAttribute>   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Оператор RemoveHandler](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Оператор RaiseEvent](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)