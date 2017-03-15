---
title: "Параметр типа &lt;имя_параметра_типа&gt; не может быть определен | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа &lt;имя_параметра_типа&gt; не может быть определен
Универсальная процедура вызывается без указания списка аргументов типов, и для одного из аргументов типа не удается определить тип.  
  
 Как правило, при вызове универсальной процедуры указывается аргумент типа для каждого параметра типа, определяемого этой процедурой. Тем не менее существует возможность полностью опустить список аргументов типов. При этом компилятор пытается определить тип каждого аргумента типа из контекста вызова. Дополнительные сведения см. в подразделе "Определение типа" в разделе [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Идентификатор ошибки:** BC36572  
  
### Исправление ошибки  
  
-   Убедитесь, что типы нормальных аргументов таковы, что определение типа согласуется с параметрами типов, объявленными для универсальной процедуры.  
  
     \-или\-  
  
-   Вызовите универсальную процедуру с полным списком аргументов типов, чтобы определение типа не требовалось.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)