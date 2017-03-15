---
title: "&quot;Exit AddHandler&quot;, &quot;Exit RemoveHandler&quot; и &quot;Exit RaiseEvent&quot; недопустимы | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Exit AddHandler&quot;, &quot;Exit RemoveHandler&quot; и &quot;Exit RaiseEvent&quot; недопустимы
"Exit AddHandler", "Exit RemoveHandler" и "Exit RaiseEvent" недопустимы. Используйте "Return" для выхода из членов\-событий.  
  
 Оператор `Exit` нельзя использовать для выхода из метода `AddHandler`, `RemoveHandler` или `RaiseEvent` в объявлении `Custom Event`. Вместо этого для выхода из метода используется оператор `Return` без указания возвращаемого выражения.  
  
 **Идентификатор ошибки:** BC31111  
  
### Исправление ошибки  
  
-   Замените оператор `Exit` на оператор `Return`.  
  
     Убедитесь в том, что для оператора `Return` не задано возвращаемое выражение.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)