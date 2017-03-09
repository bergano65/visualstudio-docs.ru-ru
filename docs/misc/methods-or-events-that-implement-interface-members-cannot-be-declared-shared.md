---
title: "Методы или события, которые реализуют члены интерфейса, не могут объявляться как &quot;Shared&quot; | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы или события, которые реализуют члены интерфейса, не могут объявляться как &quot;Shared&quot;
Вы попытались объявить метод или событие, реализующее член интерфейса, как `Shared`. Модификаторы `Shared` или `Private` недопустимы для методов или событий, реализуемых в классе, за исключением класса с запретом наследования.  
  
 **Идентификатор ошибки:** BC30505  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Shared`.  
  
## См. также  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)