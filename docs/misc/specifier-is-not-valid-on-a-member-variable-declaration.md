---
title: "&quot;&lt;спецификатор&gt;&quot; является недопустимым объявлением переменной-члена | Microsoft Docs"
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
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;спецификатор&gt;&quot; является недопустимым объявлением переменной-члена
Инструкция `Dim` содержит недопустимое ключевое слово. Инструкция `Dim` может содержать только ключевые слова `Friend`, `Private`, `Protected`, `Public`, `ReadOnly`, `Shadows`, `Shared` или `Static`.  
  
 Это сообщение также может появиться, если объявить переменную `Static` вне процедуры. Оператор `Static` можно использовать только на уровне процедуры.  
  
 Обратите внимание, что при включении допустимого ключевого слова в инструкцию `Dim` можно опустить ключевое слово `Dim`.  
  
 **Идентификатор ошибки:** BC30235  
  
### Исправление ошибки  
  
1.  Удалите недопустимое ключевое слово из оператора `Dim`.  
  
2.  Если вы объявили переменную `Static` вне процедуры, либо переместите объявление в процедуру, либо удалите ключевое слово `Static`.  
  
## См. также  
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)