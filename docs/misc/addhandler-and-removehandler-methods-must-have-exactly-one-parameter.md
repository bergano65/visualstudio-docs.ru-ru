---
title: "Методы AddHandler и RemoveHandler должны иметь ровно один параметр. | Microsoft Docs"
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
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы AddHandler и RemoveHandler должны иметь ровно один параметр.
Объявление настраиваемого события должно иметь объявления `AddHandler` или `RemoveHandler`, каждое из которых принимает единственный параметр типа делегата, указанный с помощью предложения `As` настраиваемого события.  
  
 **Идентификатор ошибки:** BC31133  
  
### Исправление ошибки  
  
-   Удалите лишние параметры из списка параметров и измените тип параметра, чтобы он совпадал с типом делегата, указанным в предложении `As` настраиваемого события.  
  
## Пример  
 В этом примере показано пользовательское событие с корректными типами параметров для объявлений `AddHandler` и `RemoveHandler`.  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler — удалить](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler — удалить](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)