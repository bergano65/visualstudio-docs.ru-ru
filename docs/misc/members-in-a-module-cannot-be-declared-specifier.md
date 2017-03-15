---
title: "Члены в модуле не могут объявляться как &quot;&lt;спецификатор&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30436"
  - "bc30436"
helpviewer_keywords: 
  - "BC30436"
ms.assetid: c0560864-64f6-4c76-803f-d9c51df89d62
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Члены в модуле не могут объявляться как &quot;&lt;спецификатор&gt;&quot;
Вы использовали спецификатор, который недопустим для члена в операторе `Module`. Нельзя создавать экземпляры модулей, модули не поддерживают наследование и не могут реализовывать интерфейсы.  
  
 **Идентификатор ошибки:** BC30436  
  
### Исправление ошибки  
  
-   Удалите спецификатор.  
  
## См. также  
 [Оператор Module](/dotnet/visual-basic/language-reference/statements/module-statement)