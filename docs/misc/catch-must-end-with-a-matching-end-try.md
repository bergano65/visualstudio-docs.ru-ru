---
title: "Блок Catch должен заканчиваться соответствующим оператором End Try | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок Catch должен заканчиваться соответствующим оператором End Try
В коде есть оператор `Catch` без соответствующего оператора `End Try`. Операторы `Catch` должны заканчиваться оператором `End Try`.  
  
 **Идентификатор ошибки:** BC30441  
  
### Исправление ошибки  
  
1.  Удалите оператор `Catch`.  
  
2.  Добавьте оператор `End Try`, чтобы завершить блок.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Общие сведения об обработке структурированных исключений для Visual Basic](http://msdn.microsoft.com/ru-ru/bb81af80-a735-4873-9711-6151a48e418a)