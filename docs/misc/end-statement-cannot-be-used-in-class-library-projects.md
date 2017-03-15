---
title: "Оператор End не может использоваться в проектах библиотек классов | Microsoft Docs"
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
  - "bc30615"
  - "vbc30615"
helpviewer_keywords: 
  - "BC30615"
ms.assetid: c8606b17-b50b-4014-b76e-b748d57e9389
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор End не может использоваться в проектах библиотек классов
В проектах библиотек классов, которые используются для создания библиотек DLL, не разрешается использование ключевого слова `End` для остановки выполнения кода в процедуре.  
  
 **Идентификатор ошибки:** BC30615  
  
### Исправление ошибки  
  
-   Используйте управляющие структуры, такие как `While` и `For`, для управления потоком выполнения программы.  
  
## См. также  
 [Управление ходом выполнения](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)