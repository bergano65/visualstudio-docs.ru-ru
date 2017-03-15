---
title: "Sub New не может обрабатывать события | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub New не может обрабатывать события
Предпринята попытка объединить `Sub New` с `Handles`, что недопустимо. Используйте ключевое слово `Handles` в конце объявления процедуры, чтобы она обрабатывала события, вызванные переменной объекта, которая объявлена с помощью ключевого слова `WithEvents`.  
  
 **Идентификатор ошибки:** BC30497  
  
### Исправление ошибки  
  
1.  Не используйте `New` в данном контексте.  
  
## См. также  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)