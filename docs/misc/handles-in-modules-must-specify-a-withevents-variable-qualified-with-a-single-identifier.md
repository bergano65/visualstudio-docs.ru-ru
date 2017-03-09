---
title: "&quot;Handles&quot; в модулях должны задавать переменную &quot;WithEvents&quot;, определенную одним идентификатором | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Handles&quot; в модулях должны задавать переменную &quot;WithEvents&quot;, определенную одним идентификатором
Для задания обработчика событий необходимо указать в операторе `Handles` объектную переменную, объявленную с ключевым словом `WithEvents`.  
  
 **Идентификатор ошибки:** BC31418  
  
### Исправление ошибки  
  
-   Используйте модификатор `WithEvents` для объявления переменных, которые будут использоваться с оператором `Handles`.  
  
## См. также  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)