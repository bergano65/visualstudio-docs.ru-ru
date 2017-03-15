---
title: "Выражение типа &quot;&lt;имя_типа&gt;&quot; не может быть преобразовано в &quot;Object&quot; или &quot;ValueType&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Выражение типа &quot;&lt;имя_типа&gt;&quot; не может быть преобразовано в &quot;Object&quot; или &quot;ValueType&quot;.
Выражение оценивается в тип, который не может быть упакован\-преобразован средой CLR.  
  
 *Упаковкой\-преобразованием* называется обработка, необходимая для преобразования типа в `Object` или, в некоторых случаях, в <xref:System.ValueType>. Среда CLR не поддерживает упаковку\-преобразование определенных типов, например <xref:System.ArgIterator> и <xref:System.TypedReference>.  
  
 Если вы не использовали `CType` или `CObj` в операторе, содержащем это выражение, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается выполнить неявное преобразование, которое вызывает эту ошибку.  
  
 **Идентификатор ошибки:** BC31394  
  
### Исправление ошибки  
  
1.  Найдите выражение, которое оценивается в указанный тип.  
  
2.  Найдите часть инструкции, в которой предпринимается попытка упаковать\-преобразовать указанный тип.  
  
3.  Перепишите эту инструкцию, чтобы исключить упаковку\-преобразование.  
  
## См. также  
 [Явные и неявные преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)