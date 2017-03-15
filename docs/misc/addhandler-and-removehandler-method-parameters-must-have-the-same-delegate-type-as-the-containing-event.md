---
title: "Параметры метода AddHandler и RemoveHandler должны иметь тот же тип делегата, что и содержащее их событие. | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметры метода AddHandler и RemoveHandler должны иметь тот же тип делегата, что и содержащее их событие.
Объявление `Custom Event` должно иметь объявления `AddHandler` или `RemoveHandler`, каждое из которых принимает единственный параметр типа делегата, указанный с помощью предложения `As` настраиваемого события.  
  
 **Идентификатор ошибки:** BC31136  
  
### Исправление ошибки  
  
-   Измените тип параметра, чтобы он совпадал с типом делегата, заданным с помощью предложения `As` настраиваемого события.  
  
## Пример  
 В этом примере показано настраиваемое событие с правильными типами параметров для объявлений `AddHandler` и `RemoveHandler`.  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## См. также  
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler — удалить](http://msdn.microsoft.com/ru-ru/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler — удалить](http://msdn.microsoft.com/ru-ru/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)