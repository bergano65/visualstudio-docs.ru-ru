---
title: "Событие &quot;&lt;имя_события&gt;&quot; с атрибутом &quot;DefaultEvent&quot; не является общедоступным для данного класса | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Событие &quot;&lt;имя_события&gt;&quot; с атрибутом &quot;DefaultEvent&quot; не является общедоступным для данного класса
Атрибут <xref:System.ComponentModel.DefaultEventAttribute> должен указывать имя открытого для доступа события в классе, к которому он применяется.  
  
 **Идентификатор ошибки:** BC30770  
  
### Исправление ошибки  
  
1.  Убедитесь в том, что класс определяет открытое для доступа событие.  
  
2.  Убедитесь в том, что имя, заданное атрибутом <xref:System.ComponentModel.DefaultEventAttribute>, соответствует имени события в классе.  
  
## См. также  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)