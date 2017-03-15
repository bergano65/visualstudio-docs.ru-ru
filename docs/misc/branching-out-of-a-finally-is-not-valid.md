---
title: "Разветвление из блока &quot;Finally&quot; недопустимо | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Разветвление из блока &quot;Finally&quot; недопустимо
Оператор `GoTo` в блоке `Finally` разветвляется за пределы блока. Не допускается переход в блок `Catch` или `Finally` и выход из этих блоков.  
  
 **Идентификатор ошибки:** BC30101  
  
### Исправление ошибки  
  
-   Удалите оператор `GoTo` и рассмотрите возможность реализации логики программы со структурами управления циклами или принятием решений.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Оператор GoTo](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Управление ходом выполнения](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)