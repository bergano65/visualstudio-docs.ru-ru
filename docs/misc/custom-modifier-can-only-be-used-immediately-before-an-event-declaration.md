---
title: "Модификатор &quot;Custom&quot; может использоваться только непосредственно перед объявлением &quot;Event&quot; | Microsoft Docs"
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
  - "vbc31140"
  - "bc31140"
helpviewer_keywords: 
  - "BC31140"
ms.assetid: e516fb5d-b11b-483b-92d0-ac7064d1841d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модификатор &quot;Custom&quot; может использоваться только непосредственно перед объявлением &quot;Event&quot;
Ключевое слово `Custom` должно предшествовать только ключевому слову `Event` в объявлении настраиваемого события.  
  
 **Идентификатор ошибки:** BC31140  
  
### Исправление ошибки  
  
-   Переместите ключевое слово `Custom`, чтобы оно было перед ключевым словом `Event`.  
  
     —или—  
  
-   Удалите ключевое слово `Custom`.  
  
## См. также  
 [Custom — удалить](http://msdn.microsoft.com/ru-ru/dc62be07-c896-4866-a533-982a661d143f)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)