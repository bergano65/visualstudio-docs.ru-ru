---
title: "Блок Finally должен заканчиваться соответствующим оператором End Try | Microsoft Docs"
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
  - "vbc30442"
  - "bc30442"
helpviewer_keywords: 
  - "BC30442"
ms.assetid: 36cce657-186c-4ba0-a760-abcef9529f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок Finally должен заканчиваться соответствующим оператором End Try
В коде есть оператор `Finally` без соответствующего оператора`End Try`. Операторы `Finally` должны заканчиваться оператором `End Try`.  
  
 **Идентификатор ошибки:** BC30442  
  
### Исправление ошибки  
  
1.  Удалите оператор `Finally`.  
  
2.  Добавьте оператор `End Try`, чтобы завершить блок.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения об обработке структурированных исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)