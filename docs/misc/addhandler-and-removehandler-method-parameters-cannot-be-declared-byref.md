---
title: "Параметры методов AddHandler и RemoveHandler не могут быть объявлены как ByRef. | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметры методов AddHandler и RemoveHandler не могут быть объявлены как ByRef.
Параметры методов `AddHandler` и `RemoveHandler` не могут объявляться с помощью модификатора `ByRef`.  
  
 **Идентификатор ошибки:** BC31134  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `ByRef` из списка параметров.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler — удалить](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler — удалить](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)