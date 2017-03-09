---
title: "Аргументы типа, определенные для метода &quot;&lt;имя_процедуры&gt;&quot;, вызвали следующие ошибки: &lt;список_ошибок&gt; | Microsoft Docs"
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
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы типа, определенные для метода &quot;&lt;имя_процедуры&gt;&quot;, вызвали следующие ошибки: &lt;список_ошибок&gt;
Универсальная процедура вызывается без указания аргументов типов, и определенные аргументы типов приводят к одному или нескольким нарушениям ограничений.  
  
 Как правило, при вызове универсального типа указывается аргумент типа для каждого параметра типа, определяемого этим универсальным типом. Если никакие аргументы типов не передаются, компилятор пытается определить типы, которые должны быть переданы параметрам типов. Если определяемые типы не удовлетворяют одному или нескольким ограничениям параметров типа, компилятор создает эту ошибку.  
  
 *Ограничение* для параметра типа ограничивает аргументы типов, которые могут быть переданы в него. Например, параметр типа может быть ограничен классом, который реализует интерфейс <xref:System.IComparable%601>. Дополнительные сведения см. в подразделе "Ограничения" раздела [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Идентификатор ошибки:** BC30954  
  
### Исправление ошибки  
  
-   Укажите аргументы типов для универсальной процедуры, чтобы компилятору не приходилось их определять.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)