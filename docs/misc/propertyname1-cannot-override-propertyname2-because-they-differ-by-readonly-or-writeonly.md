---
title: "Свойство &quot;&lt;имя_свойства1&gt;&quot; не может переопределять &quot;&lt;имя_свойства2&gt;&quot;, так как они отличаются по &quot;ReadOnly&quot; или &quot;WriteOnly&quot;. | Microsoft Docs"
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
  - "vbc30362"
  - "bc30362"
helpviewer_keywords: 
  - "BC30362"
ms.assetid: 883deb25-e6db-403e-8c03-f580baf1afa9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство &quot;&lt;имя_свойства1&gt;&quot; не может переопределять &quot;&lt;имя_свойства2&gt;&quot;, так как они отличаются по &quot;ReadOnly&quot; или &quot;WriteOnly&quot;.
Предпринята попытка переопределения одного свойства другим, отличающимся от первого только по `ReadOnly` или `WriteOnly`.  
  
 **Идентификатор ошибки:** BC30362  
  
### Исправление ошибки  
  
-   Убедитесь, что свойства отличаются друг от друга не только по `ReadOnly` и `WriteOnly`.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)