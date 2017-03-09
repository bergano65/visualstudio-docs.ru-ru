---
title: "&lt;ошибка&gt;: &quot;&lt;имя_конструктора1&gt;&quot; вызывает &quot;&lt;имя_конструктора2&gt;&quot; | Microsoft Docs"
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
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;ошибка&gt;: &quot;&lt;имя_конструктора1&gt;&quot; вызывает &quot;&lt;имя_конструктора2&gt;&quot;
Обнаружен циклический вызов конструктора. Конструктор совершает вызов `Me.New()` или `MyClass.New()`. Возможной причиной этого может быть попытка вызова перегруженного конструктора с другим списком аргументов.  
  
 **Идентификатор ошибки:** BC30297  
  
### Исправление ошибки  
  
-   Используйте другой список аргументов для вызова перегруженного конструктора.  
  
-   Если нет доступных перегрузок, то удалите вызов `Me.New()` или `MyClass.New()`.  
  
## См. также  
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)