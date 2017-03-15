---
title: "&quot;&lt;объявление1&gt;&quot; не может переопределять &quot;&lt;объявление2&gt;&quot;, поскольку оно объявлено как &quot;NotOverridable&quot; | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;объявление1&gt;&quot; не может переопределять &quot;&lt;объявление2&gt;&quot;, поскольку оно объявлено как &quot;NotOverridable&quot;
Объявление процедуры или свойства пытается переопределить наследуемый элемент с тем же именем, однако наследуемый элемент был определен как `NotOverridable`.  
  
 **Идентификатор ошибки:** BC30267  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `NotOverridable` из объявления наследуемого элемента или удалите объявление переопределения.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)