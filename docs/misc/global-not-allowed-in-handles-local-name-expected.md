---
title: "&quot;Global&quot; нельзя использовать в обработчиках; ожидается локальное имя | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Global&quot; нельзя использовать в обработчиках; ожидается локальное имя
Предложение `Handles` должно ссылаться на локальное событие. Ключевое слово `Global` предоставляет доступ к глобальным программным элементам.  
  
 **Идентификатор ошибки:** BC36002  
  
### Исправление ошибки  
  
-   Измените предложение `Handles` так, чтобы оно ссылалось на локальный экземпляр события вместо глобального.  
  
## См. также  
 [Global \- delete](http://msdn.microsoft.com/ru-ru/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)