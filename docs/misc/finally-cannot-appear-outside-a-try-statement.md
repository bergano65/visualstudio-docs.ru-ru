---
title: "Finally не может находиться за пределами оператора Try | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Finally не может находиться за пределами оператора Try
Оператор `Finally` используется для завершения блока `Try...Catch...Finally`, поэтому он может присутствовать только один раз в конце блока. В коде есть ненужный оператор `Finally` или оператор `Finally` находится за пределами границ соответствующего блока `Try`.  
  
 **Идентификатор ошибки:** BC30382  
  
### Исправление ошибки  
  
1.  Найдите и удалите ненужный оператор `Finally`.  
  
2.  Переместите оператор `Finally` в правильное место в своем коде.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения об обработке структурированных исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)