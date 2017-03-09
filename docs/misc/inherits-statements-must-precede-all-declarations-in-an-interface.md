---
title: "Операторы &quot;Inherits&quot; должны предшествовать всем объявлениям в интерфейсе | Microsoft Docs"
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
  - "bc30357"
  - "vbc30357"
helpviewer_keywords: 
  - "BC30357"
ms.assetid: 730481dc-cbf8-430f-80d0-03b1cdcc0c79
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Операторы &quot;Inherits&quot; должны предшествовать всем объявлениям в интерфейсе
Оператор `Inherits` должен быть первой непустой и незакомментированной строкой в определении класса.  
  
 **Идентификатор ошибки:** BC30357  
  
### Исправление ошибки  
  
-   Переместите оператор `Inherits` так, чтобы он находился перед всеми объявлениями.  
  
## См. также  
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)