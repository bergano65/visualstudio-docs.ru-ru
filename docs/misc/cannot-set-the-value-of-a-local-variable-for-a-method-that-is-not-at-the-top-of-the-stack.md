---
title: "Невозможно задать значение локальной переменной для метода, который не является верхним элементом стека | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно задать значение локальной переменной для метода, который не является верхним элементом стека
Переменные можно изменять только в том случае, если они являются верхними элементами стека вызовов. Например, если `procedure1` вызывает `procedure2` и вы находитесь в `procedure1`, то не сможете изменить переменные в `procedure2`.  
  
 **Идентификатор ошибки:** BC30711  
  
### Исправление ошибки  
  
-   Измените переменные, находящиеся вверху стека вызовов.  
  
## См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)