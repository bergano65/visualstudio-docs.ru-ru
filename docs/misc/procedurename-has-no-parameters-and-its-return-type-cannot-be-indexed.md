---
title: "Процедура &quot;&lt;имя_процедуры&gt;&quot; не имеет параметров, и ее тип возврата не может быть проиндексирован. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32016"
  - "vbc32016"
helpviewer_keywords: 
  - "BC32016"
ms.assetid: beead513-c237-4c04-8a18-56f075b84712
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Процедура &quot;&lt;имя_процедуры&gt;&quot; не имеет параметров, и ее тип возврата не может быть проиндексирован.
Вызов процедуры `Function` или `Sub` предоставляет один или несколько аргументов, но процедура не принимает никакие аргументы, и ее тип возврата \(если это `Function`\) не является типом массива.  
  
 **Идентификатор ошибки:** BC32016  
  
### Исправление ошибки  
  
-   Удалите аргумент или аргументы из вызова процедуры.  
  
## См. также  
 [Подпрограммы](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Оператор Function](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Оператор Sub](/dotnet/visual-basic/language-reference/statements/sub-statement)