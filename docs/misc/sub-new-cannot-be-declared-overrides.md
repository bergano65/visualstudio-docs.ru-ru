---
title: "Sub New не может объявляться с модификатором Overrides | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub New не может объявляться с модификатором Overrides
В конструкторе указано, что он переопределяет унаследованный конструктор. Конструкторы не переопределяются.  
  
 **Идентификатор ошибки:** BC30283  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Overrides` из объявления `Sub`.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)