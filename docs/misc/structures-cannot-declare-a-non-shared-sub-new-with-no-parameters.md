---
title: "В структурах не могут объявляться не используемые совместно Sub New без параметров. | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В структурах не могут объявляться не используемые совместно Sub New без параметров.
Конструкторы `Sub New`, объявляемые в структурах, должны либо принимать аргументы, либо объявляться с модификатором `Shared`.  
  
 **Идентификатор ошибки**: BC30629  
  
### Исправление ошибки  
  
-   Измените конструктор `Sub New`, чтобы он принимал аргументы.  
  
-   Примените модификатор `Shared`, чтобы сделать этот конструктор общим.  
  
## См. также  
 [Оператор Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Структуры](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)