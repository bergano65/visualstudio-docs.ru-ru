---
title: "Свойство &quot;&lt;имя_свойства&gt;&quot; должно быть объявлено как Default, так как оно переопределяет свойство по умолчанию в базовом &quot;&lt;имя&gt;&quot; | Microsoft Docs"
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
  - "bc30360"
  - "vbc30360"
helpviewer_keywords: 
  - "BC30360"
ms.assetid: 6acbf77c-247e-4e49-9784-4c05cc0df748
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство &quot;&lt;имя_свойства&gt;&quot; должно быть объявлено как Default, так как оно переопределяет свойство по умолчанию в базовом &quot;&lt;имя&gt;&quot;
Оператор `Property` в коде переопределяет свойство `Default` базового класса, структуры или интерфейса, и поэтому переопределяющее свойство должно быть объявлено как `Default`.  
  
 **Идентификатор ошибки:** BC30360  
  
### Исправление ошибки  
  
-   Объявите свойство `Default`.  
  
## См. также  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)