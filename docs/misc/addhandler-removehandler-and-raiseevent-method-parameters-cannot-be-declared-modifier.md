---
title: "Параметры методов AddHandler, RemoveHandler и RaiseEvent не могут быть объявлены как &quot;&lt;модификатор&gt;&quot; | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметры методов AddHandler, RemoveHandler и RaiseEvent не могут быть объявлены как &quot;&lt;модификатор&gt;&quot;
Параметры методов `AddHandler`, `RemoveHandler` и `RaiseEvent` не могут объявляться с помощью модификаторов `Optional` или `ParamArray`.  
  
 Модификаторы `Optional` и `ParamArray` разрешены только для параметров в объявлениях `Declare`, `Function`, `Property` и `Sub`.  
  
 **Идентификатор ошибки:** BC31138  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Optional` или `ParamArray` из списка параметров.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)