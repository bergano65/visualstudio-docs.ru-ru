---
title: "Недопустимо использовать именованные аргументы как индексы массива | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимо использовать именованные аргументы как индексы массива
Индекс массива задается с помощью синтаксиса передачи аргумента процедуры по имени, например `Array(Index := 10)`. Использование этого синтаксиса для индексов массива не допускается.  
  
 **Идентификатор ошибки:** BC30075  
  
### Исправление ошибки  
  
-   Используйте в качестве индекса массива обычное выражение переменной или константы, например `Array(10)`.  
  
## См. также  
 [НЕ В СБОРКЕ. Обзор массивов в Visual Basic](http://msdn.microsoft.com/ru-ru/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Передача аргументов по позиции и по имени](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)