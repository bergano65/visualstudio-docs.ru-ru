---
title: "Метод не может одновременно содержать оператор Try и оператор On Error или Resume. | Microsoft Docs"
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
  - "vbc30544"
  - "bc30544"
helpviewer_keywords: 
  - "BC30544"
ms.assetid: 1e75d5fe-9a6b-43c2-9749-1f2d7ce5b10d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод не может одновременно содержать оператор Try и оператор On Error или Resume.
Вы объединили оператор `Try` с `On Error` или `Resume`.  
  
 **Идентификатор ошибки:** BC30544  
  
### Исправление ошибки  
  
1.  Удалите `On Error` или `Resume`.  
  
## См. также  
 [Общие сведения об обработке структурированных исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)