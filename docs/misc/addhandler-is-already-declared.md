---
title: "AddHandler уже объявлен | Microsoft Docs"
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
  - "bc31127"
  - "vbc31127"
helpviewer_keywords: 
  - "BC31127"
ms.assetid: 70ecd206-449e-4ae0-bf6a-980c40d8d847
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# AddHandler уже объявлен
Несколько объявлений `AddHandler` в объявлении пользовательского события. Объявление `AddHandler` объявляет процедуру, используемую для добавления обработчика событий.  
  
 **Идентификатор ошибки:** BC31127  
  
### Исправление ошибки  
  
-   Удалите лишний оператор `AddHandler`.  
  
## См. также  
 [Оператор AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement)