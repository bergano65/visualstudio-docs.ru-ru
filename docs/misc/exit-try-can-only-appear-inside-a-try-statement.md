---
title: "Exit Try может использоваться только в теле оператора Try | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exit Try может использоваться только в теле оператора Try
Оператор `Exit Try` может присутствовать только в операторе блока `Try`. Либо в коде есть лишний оператор `Exit Try`, либо оператор `Exit Try` находится за пределами границ соответствующего блока `Try`.  
  
 **Идентификатор ошибки:** BC30393  
  
### Исправление ошибки  
  
1.  Найдите и удалите ненужный оператор `Exit Try`.  
  
2.  Переместите оператор `Exit Try`в правильное место в коде.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения о структурированной обработке исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)