---
title: "&lt;тип1&gt; &quot;&lt;имя_типа&gt;&quot; не может объявляться с модификатором Overrides, поскольку не переопределяет &lt;тип1&gt; в базовом классе &lt;тип2&gt; | Microsoft Docs"
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
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;тип1&gt; &quot;&lt;имя_типа&gt;&quot; не может объявляться с модификатором Overrides, поскольку не переопределяет &lt;тип1&gt; в базовом классе &lt;тип2&gt;
В операторе `Sub`, `Function` или `Property` указывается модификатор `Overrides`, но в базовом классе не существует типа с тем же именем.  
  
 **Идентификатор ошибки:** BC30284  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания имени типа.  
  
2.  Удалите лишнее ключевое слово `Overrides`.  
  
## См. также  
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)