---
title: "Наследование от &quot;System.&lt;имя_класса&gt;&quot; недопустимо | Microsoft Docs"
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
  - "vbc30015"
  - "bc30015"
helpviewer_keywords: 
  - "BC30015"
ms.assetid: b4c005df-a510-47c7-b5cc-27f4514d32b6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Наследование от &quot;System.&lt;имя_класса&gt;&quot; недопустимо
Класс не может наследовать от `System.Array`, `System.Delegate`, `System.Enum` или `System.ValueType`.  
  
 **Идентификатор ошибки:** BC30015  
  
### Исправление ошибки  
  
-   Удалите оператор `Inherits` или измените его для наследования от допустимого базового класса.  
  
## См. также  
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Объявление переменных объектов](/dotnet/visual-basic/programming-guide/language-features/variables/object-variable-declaration)