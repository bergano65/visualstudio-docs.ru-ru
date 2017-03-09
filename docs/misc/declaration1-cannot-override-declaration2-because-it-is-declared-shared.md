---
title: "&quot;&lt;объявление1&gt;&quot; не может переопределять &quot;&lt;объявление2&gt;&quot;, поскольку он объявлен как &quot;Shared&quot; | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;объявление1&gt;&quot; не может переопределять &quot;&lt;объявление2&gt;&quot;, поскольку он объявлен как &quot;Shared&quot;
Объявление процедуры или свойства пытается переопределить наследуемый элемент с тем же именем, однако наследуемый элемент был определен как `Shared`. Общие элементы не связаны ни с одним экземпляром класса, поэтому их нельзя переопределить.  
  
 **Идентификатор ошибки:** BC30268  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Shared` из наследуемого элемента или удалите объявление переопределения.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)