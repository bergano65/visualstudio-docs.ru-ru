---
title: "Оператор не объявляет метод AddHandler, RemoveHandler или RaiseEvent. | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не объявляет метод AddHandler, RemoveHandler или RaiseEvent.
Оператор не предоставляет оператор объявления `AddHandler`, `RemoveHandler` или `RaiseEvent` для процедуры `Custom Event`. Объявление настраиваемого события — это блок кода, заключенный в операторы `Custom Event` и `End Event`. Внутри этого блока каждая процедура `Custom Event` представляет собой внутренний блок, заключенный в оператор объявления и оператор `End`.  
  
 **Идентификатор ошибки:** BC31113  
  
### Исправление ошибки  
  
-   Предоставьте оператор объявления `AddHandler`, `RemoveHandler` или `RaiseEvent`.  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler — удалить](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler — удалить](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent — удалить](http://msdn.microsoft.com/ru-ru/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)