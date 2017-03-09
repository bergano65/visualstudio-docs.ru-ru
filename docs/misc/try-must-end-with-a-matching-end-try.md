---
title: "Блок Try должен заканчиваться соответствующим End Try. | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок Try должен заканчиваться соответствующим End Try.
Оператор `Try` используется для инициации блока `Try`, поэтому он может располагаться только в начале блока, а соответствующий оператор `End Try` должен завершать этот блок. Либо имеется лишний оператор `Try`, либо блок `Try` не был завершен с помощью `Finally`.  
  
 **Идентификатор ошибки:** BC30384  
  
### Исправление ошибки  
  
1.  Найдите и удалите лишний `Try` или завершите блок с соответствующим `End Try`.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения о структурированной обработке исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)