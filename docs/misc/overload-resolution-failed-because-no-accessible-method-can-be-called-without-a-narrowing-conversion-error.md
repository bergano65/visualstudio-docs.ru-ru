---
title: "Сбой при разрешении перегрузки, так как ни один из доступных &quot;&lt;метод&gt;&quot; не может быть вызван без преобразования, сужающего диапазон значений: &lt;ошибка&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Сбой при разрешении перегрузки, так как ни один из доступных &quot;&lt;метод&gt;&quot; не может быть вызван без преобразования, сужающего диапазон значений: &lt;ошибка&gt;
Вы выполнили вызов перегруженного метода, но компилятор не в состоянии найти метод, который можно вызывать без преобразования сужения. Преобразование сужения изменяет тип данных значения на тип, который не сможет точно содержать возможные значения.  
  
 **Идентификатор ошибки:** BC30519  
  
### Исправление ошибки  
  
-   Задайте имя `Option Strict Off`.  
  
## См. также  
 [Перегруженные свойства и методы](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)