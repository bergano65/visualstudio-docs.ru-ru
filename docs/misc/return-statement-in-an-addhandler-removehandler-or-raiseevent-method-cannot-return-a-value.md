---
title: "Оператор &quot;Return&quot; в методах &quot;AddHandler&quot;, &quot;RemoveHandler&quot; и &quot;RaiseEvent&quot; не может возвращать значение | Microsoft Docs"
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
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;Return&quot; в методах &quot;AddHandler&quot;, &quot;RemoveHandler&quot; и &quot;RaiseEvent&quot; не может возвращать значение
Методы `AddHandler`, `RemoveHandler` и `RaiseEvent` в объявлении `Custom Event` могут содержать операторы `Return` для завершения методов. Однако в операторе `Return` нельзя указать возвращаемое значение, так как методы не могут возвращать значения.  
  
 **Идентификатор ошибки:** BC30940  
  
### Исправление ошибки  
  
-   Удалите выражение, следующее за оператором `Return`.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)